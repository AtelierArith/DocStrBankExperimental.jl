```julia
rand(
    distribution::ExperimentalDesign.CategoricalFactor
) -> Vector
rand(
    distribution::ExperimentalDesign.CategoricalFactor,
    n::Int64
) -> Vector

```

```jldoctest
julia> rand(CategoricalFactor([:a, :b, 2, 1.0]), 6)
6-element Vector{Any}:
 2
 1.0
  :b
 2
 2
 1.0

```
