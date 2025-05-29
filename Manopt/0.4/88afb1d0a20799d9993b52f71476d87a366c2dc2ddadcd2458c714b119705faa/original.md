```
KKTVectorFieldNormSqGradient{O<:ConstrainedManifoldObjective}
```

Compute the gradient of the [`KKTVectorFieldNormSq`](@ref) $φ(p,μ,λ,s) = \lVert F(p,μ,λ,s)\rVert^2$, that is of the norm squared of the [`KKTVectorField`](@ref) $F$.

This is given in [LaiYoshise:2024](@cite) as the gradient of their merit function, which we can write with the adjoint $J^*$ of the Jacobian

$$
\operatorname{grad} φ = 2\operatorname{J}^* F(p, μ, λ, s)[F(p, μ, λ, s)],
$$

and hence is computed with [`KKTVectorFieldAdjointJacobian`](@ref) and [`KKTVectorField`](@ref).

For completeness, the gradient reads, using the [`LagrangianGradient`](@ref) $L = \operatorname{grad}_p \mathcal L(p,μ,λ) ∈ T_p\mathcal M$, for a shorthand of the first component of $F$, as

$$
\operatorname{grad} φ
=
2 \begin{pmatrix}
\operatorname{grad}_p \mathcal L(p,μ,λ)[L] + (g_i(p) + s_i)\operatorname{grad} g_i(p) + h_j(p)\operatorname{grad} h_j(p)\\
  \Bigl( ⟨\operatorname{grad} g_i(p), L⟩ + s_i\Bigr)_{i=1}^m + μ ⊙ s ⊙ s\\
  \Bigl( ⟨\operatorname{grad} h_j(p), L⟩ \Bigr)_{j=1}^n\\
  g + s + μ ⊙ μ ⊙ s
\end{pmatrix},
$$

where $⊙$ denotes the Hadamard (or elementwise) product.

# Fields

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)

# Constructor

```
KKTVectorFieldNormSqGradient(cmo::ConstrainedManifoldObjective)
```

# Example

Define `grad_f = KKTVectorFieldNormSqGradient(cmo)` for some [`ConstrainedManifoldObjective`](@ref) `cmo` and let `N` be the product manifold of $\mathcal M×ℝ^m×ℝ^n×ℝ^m$. Then, you can call this cost as `grad_f(N, q)` or as the in-place variant `grad_f(N, Y, q)`, where `q` is a point on `N` and `Y` is a tangent vector at `q` returning the resulting gradient at.
