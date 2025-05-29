```julia
struct Galerkin <: CalculustCore.Spaces.AbstractDiscretization
```

The `Galerkin` discretization is a weighted residual method where the trial space is equal to the test space.
