```
taylorsolve(H::Array{CPType,2}, x::Vector{CPType}, k::Int, t::Real) -> ArrayReg, CPType
```

Simulates a Hamiltonian using the Taylor truncation method. Returns the state register and inverse probability of finding it.
