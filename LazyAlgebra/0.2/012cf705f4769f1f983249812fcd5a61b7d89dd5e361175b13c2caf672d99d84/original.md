```
multiplier(A)
```

yields the multiplier `λ` of the scaled mapping `A = λ*M` (see [`Scaled`](@ref)); otherwise yields `1`. Note that this method also works for intances of `LinearAlgebra.UniformScaling`. Call [`unscaled`](@ref) to get the mapping `M`. `λ`.
