```julia
CategoricalFactor(
    values::Array{N, 1}
) -> ExperimentalDesign.CategoricalFactor

```

```jldoctest
julia> a = CategoricalFactor([:a, :b, 2, 1.0])
CategoricalFactor(
values: Any[:a, :b, 2, 1.0]
distribution: DiscreteUniform(a=1, b=4)
)

```
