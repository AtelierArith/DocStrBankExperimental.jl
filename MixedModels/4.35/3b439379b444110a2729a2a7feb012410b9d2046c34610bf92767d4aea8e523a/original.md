```
modelmatrix(m::MixedModel)
```

Returns the model matrix `X` for the fixed-effects parameters, as returned by [`coef`](@ref).

This is always the full model matrix in the original column order and from a field in the model struct.  It should be copied if it is to be modified.
