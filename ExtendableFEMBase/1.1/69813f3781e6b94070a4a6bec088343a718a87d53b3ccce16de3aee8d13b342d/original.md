```julia
struct FEVector{T, Tv, Ti}
```

a plain array but with an additional layer of several FEVectorBlock subdivisions each carrying coefficients for their associated FESpace. The j-th block can be accessed by getindex(::FEVector, j) or by getindex(::FEVector, tag) if tags are associated. The full vector can be accessed via FEVector.entries 
