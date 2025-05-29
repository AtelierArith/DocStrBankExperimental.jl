```
TemperatureREMD(; <keyword arguments>)
```

A simulator for a parallel temperature replica exchange MD (T-REMD) simulation on a [`ReplicaSystem`](@ref).

See [Sugita and Okamoto 1999](https://doi.org/10.1016/S0009-2614(99)01123-9). The corresponding [`ReplicaSystem`](@ref) should have the same number of replicas as the number of temperatures in the simulator. When calling [`simulate!`](@ref), the `assign_velocities` keyword argument determines whether to assign random velocities at the appropriate temperature for each replica.

# Arguments

  * `dt::DT`: the time step of the simulation.
  * `temperatures::TP`: the temperatures corresponding to the replicas.
  * `simulators::ST`: individual simulators for simulating each replica.
  * `exchange_time::ET`: the time interval between replica exchange attempts.
