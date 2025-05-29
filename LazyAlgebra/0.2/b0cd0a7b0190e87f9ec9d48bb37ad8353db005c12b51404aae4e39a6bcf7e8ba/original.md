```
unscaled(A)
```

yields the mapping `M` of the scaled mapping `A = λ*M` (see [`Scaled`](@ref)); otherwise yields `A`. This method also works for intances of `LinearAlgebra.UniformScaling`. Call [`multiplier`](@ref) to get the multiplier `λ`.
