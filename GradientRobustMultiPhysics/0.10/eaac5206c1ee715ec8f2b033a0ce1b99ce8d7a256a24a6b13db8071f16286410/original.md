```julia
struct FEVector{T, Tv, Ti}
```

a plain array but with an additional layer of several FEVectorBlock subdivisions each carrying coefficients for their associated FESpace
