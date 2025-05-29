```
flux(u, normal_direction::AbstractVector, equations::AbstractEquations{1})
```

Enables calling `flux` with a non-integer argument `normal_direction` for one-dimensional equations. Returns the value of `flux(u, 1, equations)` scaled by `normal_direction[1]`.
