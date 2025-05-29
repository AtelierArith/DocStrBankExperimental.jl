```
QuasiNewtonLimitedMemoryDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

This [`AbstractQuasiNewtonDirectionUpdate`](@ref) represents the limited-memory Riemannian BFGS update, where the approximating operator is represented by $m$ stored pairs of tangent vectors $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$ in the $k$-th iteration. For the calculation of the search direction $η_k$, the generalisation of the two-loop recursion is used (see [HuangGallivanAbsil:2015](@cite)), since it only requires inner products and linear combinations of tangent vectors in $T_{x_k} \mathcal{M}$. For that the stored pairs of tangent vectors $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$, the gradient $\operatorname{grad}f(x_k)$ of the objective function $f$ in $x_k$ and the positive definite self-adjoint operator

$$
\mathcal{B}^{(0)}_k[⋅] = \frac{g_{x_k}(s_{k-1}, y_{k-1})}{g_{x_k}(y_{k-1}, y_{k-1})} \; \mathrm{id}_{T_{x_k} \mathcal{M}}[⋅]
$$

are used. The two-loop recursion can be understood as that the [`InverseBFGS`](@ref) update is executed $m$ times in a row on $\mathcal{B}^{(0)}_k[⋅]$ using the tangent vectors $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$, and in the same time the resulting operator $\mathcal{B}^{LRBFGS}_k [⋅]$ is directly applied on $\operatorname{grad}f(x_k)$. When updating there are two cases: if there is still free memory, $k < m$, the previously stored vector pairs $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$ have to be transported into the upcoming tangent space $T_{x_{k+1}} \mathcal{M}$. If there is no free memory, the oldest pair $\{ \widetilde{s}_{k−m}, \widetilde{y}_{k−m}\}$ has to be discarded and then all the remaining vector pairs $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m+1}^{k-1}$ are transported into the tangent space $T_{x_{k+1}} \mathcal{M}$. After that the new values $s_k = \widetilde{s}_k = T^{S}_{x_k, α_k η_k}(α_k η_k)$ and $y_k = \widetilde{y}_k$ are stored at the beginning. This process ensures that new information about the objective function is always included and the old, probably no longer relevant, information is discarded.

# Provided functors

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction in-place of `η`

# Fields

  * `memory_s`                the set of the stored (and transported) search directions times step size $\{ \widetilde{s}_i\}_{i=k-m}^{k-1}$.
  * `memory_y`                set of the stored gradient differences $\{ \widetilde{y}_i\}_{i=k-m}^{k-1}$.
  * `ξ`                       a variable used in the two-loop recursion.
  * `ρ`                       a variable used in the two-loop recursion.
  * `scale`                   initial scaling of the Hessian
  * `vector_transport_method` a `AbstractVectorTransportMethod`
  * `message`                 a string containing a potential warning that might have appeared

# Constructor

```
QuasiNewtonLimitedMemoryDirectionUpdate(
    M::AbstractManifold,
    x,
    update::AbstractQuasiNewtonUpdateRule,
    memory_size;
    initial_vector=zero_vector(M,x),
    scale::Real=1.0
    project::Bool=true
)
```

# See also

[`InverseBFGS`](@ref) [`QuasiNewtonCautiousDirectionUpdate`](@ref) [`AbstractQuasiNewtonDirectionUpdate`](@ref)
