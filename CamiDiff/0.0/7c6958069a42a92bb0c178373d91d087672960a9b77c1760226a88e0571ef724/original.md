```
fdiff_interpolation_expansion_polynom(σ::T [, k=3 [, notation=bwd]]) where T<:Real
```

Finite-difference expansion coefficient vector defining the $k^{th}$-order (default *third* order) Lagrange-polynomial interpolation of a tabulated analytic function $f[n]$ at offset $σ$ with respect to index position $n$, which is positive for increasing index and negative for decreasing index.

**Forward difference notation** (`notation = fwd`)

In this case we consider the tabulated interval $f[n:n+k]$. The interpolated value $f[n-σ]$ is given by the forward-difference expansion

$$
f[n-σ] = \sum_{p=0}^k α_p(σ) Δ^p f[n] + ⋯,
$$

where the expansion coefficients are given by

[`fdiff_interpolation_expansion_polynom(σ, k, fwd)`](@ref) $→ α(σ) ≡ [α_0(σ),⋯\ α_k(σ)]$. 

Application: This polynom can serve to predict `f[n-1]` by *extrapolation* (using $σ=1$)  if `f[n:n+k]` are known. More generally, it can serve to *interpolate* to (real) positions  $n ≤ v ≤ n+k$ (using $-k ≤ σ ≤ 0$) and predict `f[n-σ]` by *extrapolation* to (real)  positions $v<n$ (using $σ > 0$) or $v>n+k$ (using $σ < -k$).  

NB. The forward offset is defined as $σ ≡ n-v$.

**Backward difference notation** (`notation = bwd`)

In this case we consider the tabulated interval $f[n-k:n]$. The interpolated value $f[n+σ]$ is given by the backward-difference expansion

$$
f[n+σ] = \sum_{p=0}^k β_p(σ) ∇^p f[n] + ⋯,
$$

where the expansion coefficients are given by

[`fdiff_interpolation_expansion_polynom(σ, k, bwd)`](@ref) $→ β(σ) ≡ [β_0(σ),⋯\ β_k(σ)]$. 

Application: This polynom can serve to predict `f[n+1]` by *extrapolation* (using $σ=1$)  if `f[n-k:n]` are known. More generally, it can serve to *interpolate* to (real) positions  $n-k ≤ v ≤ n$ (using $-k ≤ σ ≤ 0$) and predict `f[n+σ]` by *extrapolation* to (real)  positions $xv<n$ (using $σ > 0$) or $v>n+k$ (using $σ < -k$). 

NB. The backward offset is defined as $σ ≡ -(n-v)$.

#### Example:

```
julia> σ = 1; # offset correponding to extrapolation

julia> α = fdiff_interpolation_expansion_polynom(σ, k, fwd); println("α = $α")
α = [1, -1, 1, -1, 1, -1]

julia> Fk = fdiff_expansion_weights(α, fwd, reg); println("Fk = $(Fk)")
Fk = [6, -15, 20, -15, 6, -1]

julia> β = fdiff_interpolation_expansion_polynom(σ, k, bwd); println("β = $β")
β = [1, 1, 1, 1, 1, 1]

julia> revBk = fdiff_expansion_weights(β, bwd, rev); println("revBk = $(revBk)")
revBk = [-1, 6, -15, 20, -15, 6]
```
