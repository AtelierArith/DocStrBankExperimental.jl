```
QuasiNewtonMatrixDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

The `QuasiNewtonMatrixDirectionUpdate` represent a quasi-Newton update rule, where the operator is stored as a matrix. A distinction is made between the update of the approximation of the Hessian, $H_k \mapsto H_{k+1}$, and the update of the approximation of the Hessian inverse, $B_k \mapsto B_{k+1}$. For the first case, the coordinates of the search direction $η_k$ with respect to a basis $\{b_i\}^{n}_{i=1}$ are determined by solving a linear system of equations

$$
\text{Solve} \quad \hat{η_k} = - H_k \widehat{\operatorname{grad}f(x_k)},
$$

where $H_k$ is the matrix representing the operator with respect to the basis $\{b_i\}^{n}_{i=1}$ and $\widehat{\operatorname{grad}f(x_k)}$ represents the coordinates of the gradient of the objective function $f$ in $x_k$ with respect to the basis $\{b_i\}^{n}_{i=1}$. If a method is chosen where Hessian inverse is approximated, the coordinates of the search direction $η_k$ with respect to a basis $\{b_i\}^{n}_{i=1}$ are obtained simply by matrix-vector multiplication

$$
\hat{η_k} = - B_k \widehat{\operatorname{grad}f(x_k)},
$$

where $B_k$ is the matrix representing the operator with respect to the basis $\{b_i\}^{n}_{i=1}$ and $\widehat{\operatorname{grad}f(x_k)}$. In the end, the search direction $η_k$ is generated from the coordinates $\hat{eta_k}$ and the vectors of the basis $\{b_i\}^{n}_{i=1}$ in both variants. The [`AbstractQuasiNewtonUpdateRule`](@ref) indicates which quasi-Newton update rule is used. In all of them, the Euclidean update formula is used to generate the matrix $H_{k+1}$ and $B_{k+1}$, and the basis $\{b_i\}^{n}_{i=1}$ is transported into the upcoming tangent space $T_{x_{k+1}} \mathcal{M}$, preferably with an isometric vector transport, or generated there.

# Provided functors

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` to compute the update direction in-place of `η`

# Fields

  * `basis`:                  an `AbstractBasis` to use in the tangent spaces
  * `matrix`:                 (`Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M))`) the matrix which represents the approximating operator.
  * `scale`:                  (`true) indicates whether the initial matrix (= identity matrix) should be scaled before the first update.
  * `update`:                 a [`AbstractQuasiNewtonUpdateRule`](@ref).
  * `vector_transport_method`: (`vector_transport_method`)an `AbstractVectorTransportMethod`

# Constructor

```
QuasiNewtonMatrixDirectionUpdate(
    M::AbstractManifold,
    update,
    basis::B=DefaultOrthonormalBasis(),
    m=Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M));
    kwargs...
)
```

## Keyword arguments

  * `scale`, `vector_transport_method` for the two fields

Generate the Update rule with defaults from a manifold and the names corresponding to the fields.

# See also

[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) [`QuasiNewtonCautiousDirectionUpdate`](@ref) [`AbstractQuasiNewtonDirectionUpdate`](@ref)
