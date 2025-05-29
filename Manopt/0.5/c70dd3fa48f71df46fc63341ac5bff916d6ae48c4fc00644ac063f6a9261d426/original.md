```
QuasiNewtonMatrixDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

The `QuasiNewtonMatrixDirectionUpdate` represent a quasi-Newton update rule, where the operator is stored as a matrix. A distinction is made between the update of the approximation of the Hessian, $H_k \mapsto H_{k+1}$, and the update of the approximation of the Hessian inverse, $B_k \mapsto B_{k+1}$. For the first case, the coordinates of the search direction $η_k$ with respect to a basis $\{b_i\}_{i=1}^{n}$ are determined by solving a linear system of equations

$$
\text{Solve} \quad \hat{η_k} = - H_k \widehat{\operatorname{grad}f(x_k)},
$$

where $H_k$ is the matrix representing the operator with respect to the basis $\{b_i\}_{i=1}^{n}$ and $\widehat{\operatorname{grad}} f(p_k)$ represents the coordinates of the gradient of the objective function $f$ in $x_k$ with respect to the basis $\{b_i\}_{i=1}^{n}$. If a method is chosen where Hessian inverse is approximated, the coordinates of the search direction $η_k$ with respect to a basis $\{b_i\}_{i=1}^{n}$ are obtained simply by matrix-vector multiplication

$$
\hat{η_k} = - B_k \widehat{\operatorname{grad}f(x_k)},
$$

where $B_k$ is the matrix representing the operator with respect to the basis $\{b_i\}_{i=1}^{n}$ and $\widehat{\operatorname{grad}} f(p_k)$. In the end, the search direction $η_k$ is generated from the coordinates $\hat{eta_k}$ and the vectors of the basis $\{b_i\}_{i=1}^{n}$ in both variants. The [`AbstractQuasiNewtonUpdateRule`](@ref) indicates which quasi-Newton update rule is used. In all of them, the Euclidean update formula is used to generate the matrix $H_{k+1}$ and $B_{k+1}$, and the basis $\{b_i\}_{i=1}^{n}$ is transported into the upcoming tangent space $T_{p_{k+1}} \mathcal M$, preferably with an isometric vector transport, or generated there.

# Provided functors

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction in-place of `η`

# Fields

  * `basis`:                  an `AbstractBasis` to use in the tangent spaces
  * `matrix`:                 the matrix which represents the approximating operator.
  * `initial_scale`:          when initialising the update, a unit matrix is used as initial approximation, scaled by this factor
  * `update`:                 a [`AbstractQuasiNewtonUpdateRule`](@ref).
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

# Constructor

```
QuasiNewtonMatrixDirectionUpdate(
    M::AbstractManifold,
    update,
    basis::B=default_basis(M),
    m=Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M));
    kwargs...
)
```

## Keyword arguments

  * `initial_scale=1.0` – this can also be deactivated by passing `nothing`.
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

Generate the Update rule with defaults from a manifold and the names corresponding to the fields.

# See also

[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref), [`QuasiNewtonCautiousDirectionUpdate`](@ref), [`AbstractQuasiNewtonDirectionUpdate`](@ref),
