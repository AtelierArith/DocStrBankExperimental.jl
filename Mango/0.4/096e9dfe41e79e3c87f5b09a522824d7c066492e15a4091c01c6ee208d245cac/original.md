```
step_iteration(task_sim::TaskSimulation, step_size_s::Real)::TaskIterationResult
```

Execute an iteration for a step of the simulation, which time is stepped with the `step_size_s`. 

Can be called repeatedly if new tasks are spawn as a result of other tasks or as result of arriving messages. 
