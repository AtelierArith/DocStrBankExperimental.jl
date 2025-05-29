```
mutable struct BranchImpedanceChange <: Perturbation
    time::Float64
    branch_type::Type{<:PSY.ACBranch}
    branch_name::String
    multiplier::Float64
end
```

A BranchImpedanceChange change the impedance of a branch by a user defined multiplier. Currently there is only support for static branches disconnection, `PowerSystems.Line` and `PowerSystems.Transformer2W`. Future releases will provide support for a Dynamic Line disconnection.

# Arguments:

  * `time::Float64` : Defines when the Branch Impedance Change will happen. This time should be inside the time span considered in the Simulation
  * `branch_tipe::Type{<:PowerSystems.ACBranch}` : Type of branch modified
  * `branch_name::String` : User defined name for identifying the branch
  * `multiplier::Float64` : User defined value for impedance multiplier.
