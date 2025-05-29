```julia
GetConductivity!(Cond::Conductivity, as::Vector{Int64}  ; get_velocity::Bool = false, get_spectral::Bool = false)
```

Calculates the full DC conductivity. Optional Booleans to calculate the velocity matrix of the Hamiltonian, calculate spectral functions also.
