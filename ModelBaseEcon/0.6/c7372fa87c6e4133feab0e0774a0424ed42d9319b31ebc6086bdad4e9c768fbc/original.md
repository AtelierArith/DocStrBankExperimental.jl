```
inverse_transformation(::Type{<:Transformation})
```

Return a `Function` that will be called to transform the simulation data after solving. See also [`transformation`](@ref).

It is expected that `transformation(T) ∘ inverse_transformation(T) == identity` and `inverse_transformation(T) ∘ transformation(T) == identity`, but these is not verified.
