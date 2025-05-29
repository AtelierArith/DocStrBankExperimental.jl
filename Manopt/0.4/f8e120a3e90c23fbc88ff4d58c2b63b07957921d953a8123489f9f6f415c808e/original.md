```
QuasiNewtonCautiousDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

These [`AbstractQuasiNewtonDirectionUpdate`](@ref)s represent any quasi-Newton update rule, which are based on the idea of a so-called cautious update. The search direction is calculated as given in [`QuasiNewtonMatrixDirectionUpdate`](@ref) or [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref), butut the update  then is only executed if

$$
\frac{g_{x_{k+1}}(y_k,s_k)}{\lVert s_k \rVert^{2}_{x_{k+1}}} ≥ θ(\lVert \operatorname{grad}f(x_k) \rVert_{x_k}),
$$

is satisfied, where $θ$ is a monotone increasing function satisfying $θ(0) = 0$ and $θ$ is strictly increasing at $0$. If this is not the case, the corresponding update is skipped, which means that for [`QuasiNewtonMatrixDirectionUpdate`](@ref) the matrix $H_k$ or $B_k$ is not updated. The basis $\{b_i\}^{n}_{i=1}$ is nevertheless transported into the upcoming tangent space $T_{x_{k+1}} \mathcal{M}$, and for [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) neither the oldest vector pair $\{ \widetilde{s}_{k−m}, \widetilde{y}_{k−m}\}$ is discarded nor the newest vector pair $\{ \widetilde{s}_{k}, \widetilde{y}_{k}\}$ is added into storage, but all stored vector pairs $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$ are transported into the tangent space $T_{x_{k+1}} \mathcal{M}$. If [`InverseBFGS`](@ref) or [`InverseBFGS`](@ref) is chosen as update, then the resulting method follows the method of [HuangAbsilGallivan:2018](@cite), taking into account that the corresponding step size is chosen.

# Provided functors

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction in-place of `η`

# Fields

  * `update`: an [`AbstractQuasiNewtonDirectionUpdate`](@ref)
  * `θ`:      a monotone increasing function satisfying $θ(0) = 0$ and $θ$ is strictly increasing at $0$.

# Constructor

```
QuasiNewtonCautiousDirectionUpdate(U::QuasiNewtonMatrixDirectionUpdate; θ = identity)
QuasiNewtonCautiousDirectionUpdate(U::QuasiNewtonLimitedMemoryDirectionUpdate; θ = identity)
```

Generate a cautious update for either a matrix based or a limited memory based update rule.

# See also

[`QuasiNewtonMatrixDirectionUpdate`](@ref) [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref)
