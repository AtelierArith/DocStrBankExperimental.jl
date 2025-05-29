```
create_simulation_container(start_time::DateTime; communication_sim::Union{Nothing,CommunicationSimulation}=nothing, task_sim::Union{Nothing,TaskSimulation}=nothing)
```

Create a simulation container. The container is intitialized with `start_time`. 

Per default the [`SimpleCommunicationSimulation`](@ref) is used for communication simulation, and [`SimpleTaskSimulation`](@ref) for simulating the tasks of agents. To replace these, `communication_sim` and respectively `task_sim` can be set.
