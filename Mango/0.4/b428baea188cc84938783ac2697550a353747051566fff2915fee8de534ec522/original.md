```
step_simulation(container::SimulationContainer, step_size_s::Real=DISCRETE_EVENT)::Union{SimulationResult,Nothing}
```

Step the simulation using a continous time-span or until the next event happens. 

For the continous simulation a `step_size_s` can be freely chosen, for the discrete event type  DISCRETE*EVENT has to be set for the `step*size_s`.
