```
extend_vpolytope_by_densitystates(
    sepPolytope::VPolytope{Float64,Array{Float64,1}},
    sepDensityStates::Array{DensityState},
    precision::Integer
)
```

Return an extended Lazysets.VPolytope representation of polytope of separable states based on given polytope `sepPolytope` and new separable `sepDensityStates` as new vertices.
