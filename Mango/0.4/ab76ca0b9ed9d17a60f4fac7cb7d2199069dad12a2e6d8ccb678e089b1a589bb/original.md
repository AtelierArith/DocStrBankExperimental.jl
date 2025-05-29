```
run_in_simulation(runnable::Function, agents::Agent, n_steps::Int; start_time::DateTime=DateTime(2000, 1, 1), step_size_s::Int=DISCRETE_EVENT)
```

Let the agents run as simulation in a simulation container.

Execute the `runnable` in [`SimulationContainer`](@ref) while the container is active to run. After the runnable the simulation container is stepped `n_steps` time with a `step_size_s` (default is discrete event). The start time can be specified using `start_time`.
