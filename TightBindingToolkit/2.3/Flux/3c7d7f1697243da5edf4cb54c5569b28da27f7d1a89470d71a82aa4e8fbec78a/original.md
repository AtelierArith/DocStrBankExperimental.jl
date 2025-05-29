```julia
GetStringPhase(Monopoles::Vector{Vector{Float64}}, r1::Vector{Float64}, r2::Vector{Float64} ;  flux::Float64 = Float64(pi)) --> ComplexF64
```

Get the Dirac string between the given `Monopoles` phase cutting the bond on the lattice between sites `r1` and `r2`.
