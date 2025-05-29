```julia
objective(glr, X, y; c)

```

Return a function computing the objective at a given point `θ`. Note that the [`apply_X`](@ref) takes care of a potential intercept.
