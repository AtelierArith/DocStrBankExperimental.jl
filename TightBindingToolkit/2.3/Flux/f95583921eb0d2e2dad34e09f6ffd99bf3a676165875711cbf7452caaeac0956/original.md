```julia
GetBondPhase(A::Function, r1::Vector{Float64}, r2::Vector{Float64} ; n::Int64 = 100, _kwargs::Dict = Dict()) --> ComplexF64
```

Returns the tight binding phase on a bond between two sites `r1` and `r2` on a lattice with a given gauge vector potential `A`.  The phase is calculated by integrating the vector potential along the bond.
