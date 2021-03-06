---
layout: page_project
title: Scalability Enhancements to FMM for Molecular Dynamics Simulations
date: 2016-01-01
updated: 2016-03-30
navbar: Research
subnavbar: Projects
project_url:
status: running
topics:
  - numerics
  - prog_lang
keywords:
  - Fast Multipole Method, tasking, MPI-3, MPI-4
head: kabadshow_i
members:
  - balaji_p
  - haensel_d
  - amer_a
---

## Research topic and goals
This joint-lab cooperation covers the topic of parallel programming and numerical algorithms.
We are especially interested in increasing the scalability (strong scaling) of the Fast Multipole Method (FMM) for very large numbers of ranks.
Therefore, we will examine and extend the JSC-developed, high-performance FMM library called FMSolvr.
This will allow us to improve the usability of the FMM Coulomb solver in molecular dynamics simulations with only a few particles per rank.
Initial research already discovered, that the current intrinsic parallel scaling limitations stem from thread synchronization (intranode) and process synchronization (internode) on large-scale systems.
We will investigate weak and delayed synchronization models, as well as node-level tasking approaches and other techniques with MPI-3 and upcoming MPI-4 extensions to alleviate some of these performance bottlenecks.

## Results for 2015/2016
The project was initiated at the JLESC meeting in November 2014 between ANL and JSC.
To provide a consistent interface for measuring and tuning parallel code performance some profound changes had to be made to the code.
We started implementing an abstract parallelization layer for the FMSolvr library.
This especially includes a flexible parallelization approach for inter-node communication via MPI.
The adopted abstraction layer allows easier replacement/improvement of different synchronization strategies within the code.
Besides the structural changes, a latency-avoiding communication scheme was implemented to improve the strong scaling.
Together with the automatic testing framework, scaling bottlenecks of the method can be investigated much easier.

## Results for 2016/2017
During the visit of David Haensel at ANL we implemented a data-driven version of the FMM on top of Argobots.
With the experience from this implementation we implemented a tasking framework with C++ standard library features.
This tasking library is specialized for communication bound problems like they arose in MD simulations.
For the fine grained resolution of dependencies we implemented a dependency resolver which is configurable at compile time via template meta programming.

## Visits and meetings
{% person haensel_d %} joined the group of {% person balaji_p %} in Mai/June 2016 to develop a tasking scheme for FMSolvr on top of Argobots. This visit was vital to the success of this project, since we require a very flexible and fine-grained tasking scheme with only minimal overhead from the tasking runtime (e.g. Argobots).

## Impact and publications
None yet.

<!--

-->
{% bibliography --cited --file jlesc.bib %}


## Future plans
Currently we are integrating the tasking framework with the communication layers. 
This enables us to control the algorithmic flow and parallelization in detail. With this MPI-enabled tasking framework we will elaborate alternative communication strategies using MPI-3 and MPI-4.

## References

{% bibliography --file external/fmm_project.bib %}
