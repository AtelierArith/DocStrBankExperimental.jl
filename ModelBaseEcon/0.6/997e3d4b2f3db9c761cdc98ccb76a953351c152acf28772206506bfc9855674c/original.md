```
transformation(::Type{<:Transformation})
```

Return a `Function` that will be substituted into the model equations and will be called to transform the input data before solving. See also [`inverse_transformation`](@ref).

It is expected that `transformation(T) ∘ inverse_transformation(T) == identity` and `inverse_transformation(T) ∘ transformation(T) == identity`, but these is not verified.
