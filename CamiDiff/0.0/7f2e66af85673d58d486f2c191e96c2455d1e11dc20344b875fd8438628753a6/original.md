```
fdiff_expansion_weights(polynom [, notation=bwd [, ordering=rev]])
```

Weights vector corresponding to the expansion coefficient vector `polynom` of a (user-defined) finite-difference expansion.

**Forward-difference notation** (`notation = fwd`)

The weights vector $F^k ≡ [F_k^k,⋯\ F_0^k]$ corresponds to the expansion coefficient  vector $α ≡ [α_0,⋯\ α_k]$ of the $k^{th}$-order *forward-difference* expansion (`polynom = α`).

$$
\sum_{p=0}^{k}α_{p}Δ^{p}f[n]
=\sum_{j=0}^{k}F_{j}^{k}f[n+j]
=F^{k} \cdot f[n:n+k],
$$

where $f[n:n+k]$ are elements of the analytic function $f$ tabulated in regular=*forward* order.

[`fdiff_expansion_weights(α, fwd, reg)`](@ref) $→ F^k ≡ [F_0^k,⋯\ F_k^k]$,

where $α ≡ [α_0,⋯\ α_k]$ has to be supplied by the user in combination with `fwd` to indicate that the weights must be evaluated in forward-difference notation.

**Backward difference notation** (`notation = bwd`)

The weights vector $\bar{B}^{k} ≡ [B_k^k,⋯\ B_0^k]$ corresponds to the expansion coefficient  vector $β ≡ [β_0,⋯\ β_k]$ of the $k^{th}$-order *backward-difference* expansion (`polynom = β`).

$$
\sum_{p=0}^{k}β_{p}∇^{p}f[n]
=\sum_{j=0}^{k}B_{j}^kf[n-j]
=\bar{B}^k \cdot f[n-k:n].
$$

where $f[n-k:n]$ are elements of the analytic function $f$ tabulated in *forward* order.

[`fdiff_expansion_weights(β, bwd, rev)`](@ref) $→ \bar{B}^{k} ≡ [B_k^k,⋯\ B_0^k]$,

where $β ≡ [β_0,⋯\ β_k]$ has to be supplied by the user in combination with `bwd` to indicate that the weights must be evaluated in backward-difference notation.

#### Example:

Consider the expansions,

$$
\begin{aligned}
f[n-1]=(1+Δ)^{-1}f[n]=(1-Δ+Δ^2-Δ^3+⋯)f[n]&=F^{k} \cdot f[n:n+k],\\
f[n+1]=(1-∇)^{-1}f[n]=(1+∇+∇^2+∇^3+⋯)f[n]&=\bar{B}^k \cdot f[n-k:n].
\end{aligned}
$$

```
julia> f = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100];

julia> α = [1,-1,1,-1,1];

julia> Fk = fdiff_expansion_weights(α, fwd, reg); println("Fk = $(Fk)")
Fk = [5, -10, 10, -5, 1]

julia> β = [1,1,1,1,1];

julia> revBk = fdiff_expansion_weights(β, bwd, rev); println("revBk = $(revBk)")
revBk = [1, -5, 10, -10, 5]

julia> Fk ⋅ f[7:11]
25

julia> revBk ⋅ f[1:5]
25

julia> f[6]
25
```
