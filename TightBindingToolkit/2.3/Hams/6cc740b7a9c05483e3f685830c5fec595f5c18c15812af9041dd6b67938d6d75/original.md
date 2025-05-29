```julia
GetVelocity!(H::Hamiltonian, bz::BZ) --> Vector{Array{Matrix{ComplexF64}, T}}
```

returns a vector of velocity matrices at each k point defined as ∂H(k)/∂k^{μ}.
