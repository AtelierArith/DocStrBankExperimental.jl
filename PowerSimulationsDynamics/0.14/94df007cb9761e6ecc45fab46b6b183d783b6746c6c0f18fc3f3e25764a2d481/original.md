```
mutable struct BranchTrip <: Perturbation
    time::Float64
    branch_type::Type{<:PowerSystems.ACBranch}
    branch_name::String
end
```

A BranchTrip completely disconnects a branch from the system. Currently there is only support for static branches disconnection, `PowerSystems.Line` and `PowerSystems.Transformer2W`. Future releases will provide support for a Dynamic Line disconnection. **Note:** Islanding is currently not supported in `PowerSimulationsDynamics.jl`. If a `BranchTrip` isolates a generation unit, the system may diverge due to the isolated generator.

# Arguments:

  * `time::Float64` : Defines when the Branch Trip will happen. This time should be inside the time span considered in the Simulation
  * `branch_tipe::Type{<:PowerSystems.ACBranch}` : Type of branch disconnected
  * `branch_name::String` : User defined name for identifying the branch
