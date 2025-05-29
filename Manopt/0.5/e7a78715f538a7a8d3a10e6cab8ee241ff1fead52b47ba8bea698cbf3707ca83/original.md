```
KKTVectorFieldJacobian{O<:ConstrainedManifoldObjective}
```

Implement the Jacobian of the vector field $F$ of the KKT-conditions, inlcuding a slack variable for the inequality constraints, see [`KKTVectorField`](@ref) and [`KKTVectorFieldAdjointJacobian`](@ref)..

$$
\operatorname{J} F(p, μ, λ, s)[X, Y, Z, W] = \begin{pmatrix}
    \operatorname{Hess}_p \mathcal L(p, μ, λ)[X] + \displaystyle\sum_{i=1}^m Y_i \operatorname{grad} g_i(p) + \displaystyle\sum_{j=1}^n Z_j \operatorname{grad} h_j(p)\\
    \Bigl( ⟨\operatorname{grad} g_i(p), X⟩ + W_i\Bigr)_{i=1}^m\\
    \Bigl( ⟨\operatorname{grad} h_j(p), X⟩ \Bigr)_{j=1}^n\\
    μ ⊙ W + s ⊙ Y
\end{pmatrix},
$$

where $⊙$ denotes the Hadamard (or elementwise) product

See also the [`LagrangianHessian`](@ref) $\operatorname{Hess}_p \mathcal L(p, μ, λ)[X]$.

# Fields

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)

# Constructor

```
KKTVectorFieldJacobian(cmo::ConstrainedManifoldObjective)
```

Generate the Jacobian of the KKT vector field related to some [`ConstrainedManifoldObjective`](@ref) `cmo`.

# Example

Define `JF = KKTVectorFieldJacobian(cmo)` for some [`ConstrainedManifoldObjective`](@ref) `cmo` and let `N` be the product manifold of $\mathcal M×ℝ^m×ℝ^n×ℝ^m$. Then, you can call this cost as `JF(N, q, Y)` or as the in-place variant `JF(N, Z, q, Y)`, where `q` is a point on `N` and `Y` and `Z` are a tangent vector at `q`.
