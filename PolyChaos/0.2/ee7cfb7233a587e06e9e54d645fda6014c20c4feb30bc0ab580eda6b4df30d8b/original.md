```
evaluatePCE(x::AbstractVector{<:Real},ξ::AbstractVector{<:Real},α::AbstractVector{<:Real},β::AbstractVector{<:Real})
```

Evaluation of polynomial chaos expansion

$$
\mathsf{x} = \sum_{i=0}^{L} x_i \phi_i{\xi_j},
$$

where `L+1 = length(x)` and $x_j$ is the $j$th sample where $j=1,\dots,m$ with `m = length(ξ)`.
