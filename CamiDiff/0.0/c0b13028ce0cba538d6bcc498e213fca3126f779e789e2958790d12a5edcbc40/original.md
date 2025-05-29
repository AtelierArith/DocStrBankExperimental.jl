```
fdiff_differentiation_expansion_polynom(σ::T [, k=5 [, notation=bwd]]) where T<:Real
```

Finite-difference expansion coefficient vector defining $k^{th}$-order *lagrangian differentiation* of the tabulated analytic function $f[n]$ at position  $v=n-σ$.

**Forward difference notation** (`notation = fwd`)

$$
\frac{df}{dσ}[n+σ]=\sum_{p=0}^kα_p(σ)Δ^{p}f[n]
$$

Offset convention: $σ = n-v$ with respect to index $n$ in tabulated interval $f[n:n+k]$

**Backward difference notation** (`notation = bwd`)

$$
\frac{df}{dσ}[n+σ]=\sum_{p=0}^kβ_p(σ)∇^{p}f[n]
$$

where $β(σ) ≡ [β_0(σ),\ ⋯,\ β_p(σ)]$

Offset convention: $σ = -(n-v)$ with respect to index $n$ in tabulated interval $f[n-k:n]$

#### Example:

```
julia> k = 5; σ = 0; # offset correponding to differentiation

julia> o = fdiff_differentiation_expansion_polynom(0, k, fwd); println(o)
Rational{Int64}[0, 1, -1//2, 1//3, -1//4, 1//5]
```
