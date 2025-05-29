```
QuasiNewtonLimitedMemoryDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

This [`AbstractQuasiNewtonDirectionUpdate`](@ref) represents the limited-memory Riemannian BFGS update, where the approximating operator is represented by $m$ stored pairs of tangent vectors $\{\widehat{s}_i\}_{i=k-m}^{k-1}$ and $\{\widehat{y}_i\}_{i=k-m}^{k-1}$ in the $k$-th iteration. For the calculation of the search direction $X_k$, the generalisation of the two-loop recursion is used (see [HuangGallivanAbsil:2015](@cite)), since it only requires inner products and linear combinations of tangent vectors in $T_{p_k}\mathcal M$. For that the stored pairs of tangent vectors $\widehat{s}_i,  \widehat{y}_i$, the gradient $\operatorname{grad} f(p_k)$ of the objective function $f$ in $p_k$ and the positive definite self-adjoint operator

$$
\mathcal{B}^{(0)}_k[⋅] = \frac{g_{p_k}(s_{k-1}, y_{k-1})}{g_{p_k}(y_{k-1}, y_{k-1})} \; \mathrm{id}_{T_{p_k} \mathcal{M}}[⋅]
$$

are used. The two-loop recursion can be understood as that the [`InverseBFGS`](@ref) update is executed $m$ times in a row on $\mathcal B^{(0)}_k[⋅]$ using the tangent vectors $\widehat{s}_i,\widehat{y}_i$, and in the same time the resulting operator $\mathcal B^{LRBFGS}_k [⋅]$ is directly applied on $\operatorname{grad}f(x_k)$. When updating there are two cases: if there is still free memory, $k < m$, the previously stored vector pairs $\widehat{s}_i,\widehat{y}_i$ have to be transported into the upcoming tangent space $T_{p_{k+1}}\mathcal M$. If there is no free memory, the oldest pair $\widehat{s}_i,\widehat{y}_i$ has to be discarded and then all the remaining vector pairs $\widehat{s}_i,\widehat{y}_i$ are transported into the tangent space $T_{p_{k+1}}\mathcal M$. After that the new values $s_k = \widehat{s}_k = T^{S}_{x_k, α_k η_k}(α_k η_k)$ and $y_k = \widehat{y}_k$ are stored at the beginning. This process ensures that new information about the objective function is always included and the old, probably no longer relevant, information is discarded.

# Provided functors

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction in-place of `η`

# Fields

  * `memory_s`:                the set of the stored (and transported) search directions times step size $\{\widehat{s}_i\}_{i=k-m}^{k-1}$.
  * `memory_y`:                set of the stored gradient differences $\{\widehat{y}_i\}_{i=k-m}^{k-1}$.
  * `ξ`:                       a variable used in the two-loop recursion.
  * `ρ`L                       a variable used in the two-loop recursion.
  * `initial_scale`:           initial scaling of the Hessian, deactivate (e.g. when using a preconditioner) by passing `nothing`
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `message`:                 a string containing a potential warning that might have appeared
  * `project!`:                a function to stabilize the update by projecting on the tangent space

# Constructor

```
QuasiNewtonLimitedMemoryDirectionUpdate(
    M::AbstractManifold,
    x,
    update::AbstractQuasiNewtonUpdateRule,
    memory_size::Int;
    initial_vector=zero_vector(M,x),
    initial_scale::Real=1.0
    project!=copyto!
)
```

# See also

[`InverseBFGS`](@ref) [`QuasiNewtonCautiousDirectionUpdate`](@ref) [`AbstractQuasiNewtonDirectionUpdate`](@ref)
