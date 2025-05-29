```
@known(def)
```

Annotate each decision taken in the previous stage. Any [`@decision`](@ref) included in a [`@stochastic_model`](@ref) definition will implicitly add `@known` annotations to subsequent stages.

## Examples

```julia
@known x₁, x₂
```

See also [`@decision`](@ref), [`@parameters`](@ref), [`@uncertain`](@ref), [`@stage`](@ref)
