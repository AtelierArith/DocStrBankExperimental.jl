```
global_rep(λY::GlobalSection{T, AT}, Δ::AbstractMatrix{T}) where {T, AT<:StiefelManifold{T}}
```

Express `Δ` (an the tangent space of `Y`) as an instance of `StiefelLieAlgHorMatrix`.

This maps an element from $T_Y\mathcal{M}$ to an element of $\mathfrak{g}^\mathrm{hor}$. 

These two spaces are isomorphic where the isomorphism where the isomorphism is established through $\lambda(Y)\in{}G$ via:

$$
T_Y\mathcal{M} \to \mathfrak{g}^{\mathrm{hor}}, \Delta \mapsto \lambda(Y)^{-1}\Omega(Y, \Delta)\lambda(Y).
$$

Also see [`GeometricMachineLearning.Ω`](@ref).

# Examples

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: _round
import Random 

Random.seed!(123)

Y = rand(StiefelManifold, 6, 3)
Δ = rgrad(Y, randn(6, 3))
λY = GlobalSection(Y)

_round(global_rep(λY, Δ); digits = 3)

# output

6×6 StiefelLieAlgHorMatrix{Float64, SkewSymMatrix{Float64, Vector{Float64}}, Matrix{Float64}}:
  0.0     0.679   1.925   0.981  -2.058   0.4
 -0.679   0.0     0.298  -0.424   0.733  -0.919
 -1.925  -0.298   0.0    -1.815   1.409   1.085
 -0.981   0.424   1.815   0.0     0.0     0.0
  2.058  -0.733  -1.409   0.0     0.0     0.0
 -0.4     0.919  -1.085   0.0     0.0     0.0
```

# Implementation

The function `global_rep` does in fact not perform the entire map $\lambda(Y)^{-1}\Omega(Y, \Delta)\lambda(Y)$ but only

$$
\Delta \mapsto \mathrm{skew}(Y^T\Delta),
$$

to get the small skew-symmetric matrix $A\in\mathcal{S}_\mathrm{skew}(n)$ and 

$$
\Delta \mapsto (\lambda(Y)_{[1:N, n:N]}^T \Delta)_{[1:(N-n), 1:n]},
$$

to get the arbitrary matrix $B\in\mathbb{R}^{(N-n)\times{}n}$.
