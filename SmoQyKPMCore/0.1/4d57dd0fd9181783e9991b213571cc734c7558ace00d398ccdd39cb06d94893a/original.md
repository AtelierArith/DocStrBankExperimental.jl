```
kpm_eval(x::T, kpm_expansion::KPMExpansion{T}) where {T<:AbstractFloat}
```

Evaluate $F(x)$ where $x$ is real number in the interval `bounds[1] < x < bound[2]`, and the function $F(\bullet)$ is represented by a Chebyshev expansion with coefficients given by the vector `coefs`.
