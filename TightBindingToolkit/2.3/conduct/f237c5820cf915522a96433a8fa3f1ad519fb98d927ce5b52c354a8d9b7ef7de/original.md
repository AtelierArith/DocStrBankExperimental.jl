```julia
SpectralFunction(H::Array{Matrix{ComplexF64}, N}, omega::Float64 ;  spread::Float64 = 1e-3):: Array{Matrix{ComplexF64}} where {N}
```

Returns the matrix spectral function given the Hamiltonian, the frequency, and the spread.
