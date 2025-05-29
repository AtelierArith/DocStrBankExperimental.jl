```
finish_init!(sim::Simulation; [distribute = true, 
             partition::Dict{AgentID, ProcessID}, 
             partition_algo = :Metis])
```

Finish the initialization phase of the simulation. 

`partition` is an option keyword and allows to specify an assignment of the agents to the individual MPI ranks. The dictonary must contain all agentids created on the rank as key, the corresponding value is the rank on which the agent "lives" after `finish_init!`.

In the case that no `partition` is given and `distribute` is set to true, the Graph will be partitioned with the given `partition_algo`. Currently two algorithms are supported:     - :Metis uses the Metis library for the graph partitioning.      - :EqualAgentNumbers just ensures that per agent type more or less       the same number of agents are distributed to each process.

`finish_init!` must be called before applying a transition function. 

!!! info
    When a simulation is run on multiple PEs, per default the graph found on rank 0 will be partitioned using Metis, and distributed to the different ranks. Which means that it's allowed to run the initialization phase on all ranks (there is no need for a mpi.isroot check), but then all added agents and edges on other ranks then 0 will be discarded. If this is not intended `distribute` must be set to false.


See also [`register_agenttype!`](@ref), [`register_edgetype!`](@ref), [`apply!`](@ref) and [`finish_simulation!`](@ref)
