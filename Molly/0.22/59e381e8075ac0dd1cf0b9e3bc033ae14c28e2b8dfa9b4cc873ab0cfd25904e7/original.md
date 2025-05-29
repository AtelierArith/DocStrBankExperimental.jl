```
HamiltonianREMD(; <keyword arguments>)
```

A simulator for a parallel Hamiltonian replica exchange MD (H-REMD) simulation on a [`ReplicaSystem`](@ref).

The replicas are expected to have different Hamiltonians, i.e. different interactions. When calling [`simulate!`](@ref), the `assign_velocities` keyword argument determines whether to assign random velocities at the appropriate temperature for each replica.

# Arguments

  * `dt::DT`: the time step of the simulation.
  * `temperature::T`: the temperatures of the simulation.
  * `simulators::ST`: individual simulators for simulating each replica.
  * `exchange_time::ET`: the time interval between replica exchange attempts.
