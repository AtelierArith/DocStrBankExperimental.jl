```
KKTVectorField{O<:ConstrainedManifoldObjective}
```

Implement the vectorfield $F$ KKT-conditions, inlcuding a slack variable for the inequality constraints.

Given the [`LagrangianCost`](@ref)

$$
\mathcal L(p; μ, λ) = f(p) + \sum_{i=1}^m μ_ig_i(p) + \sum_{j=1}^n λ_jh_j(p)
$$

the [`LagrangianGradient`](@ref)

$$
\operatorname{grad}\mathcal L(p, μ, λ) = \operatorname{grad}f(p) + \sum_{j=1}^n λ_j \operatorname{grad} h_j(p) + \sum_{i=1}^m μ_i \operatorname{grad} g_i(p),
$$

and introducing the slack variables $s=-g(p) ∈ ℝ^m$ the vector field is given by

$$
F(p, μ, λ, s) = \begin{pmatrix}
\operatorname{grad}_p \mathcal L(p, μ, λ)\\
g(p) + s\\
h(p)\\
μ ⊙ s
\end{pmatrix}, \text{ where } p \in \mathcal M, μ, s \in ℝ^m\text{ and } λ \in ℝ^n,
$$

where $⊙$ denotes the Hadamard (or elementwise) product

# Fields

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)

While the point `p` is arbitrary and usually not needed, it serves as internal memory in the computations. Furthermore Both fields together also calrify the product manifold structure to use.

# Constructor

```
KKTVectorField(cmo::ConstrainedManifoldObjective)
```

# Example

Define `F = KKTVectorField(cmo)` for some [`ConstrainedManifoldObjective`](@ref) `cmo` and let `N` be the product manifold of $\mathcal M×ℝ^m×ℝ^n×ℝ^m$. Then, you can call this cost as `F(N, q)` or as the in-place variant `F(N, Y, q)`, where `q` is a point on `N` and `Y` is a tangent vector at `q` for the result.
