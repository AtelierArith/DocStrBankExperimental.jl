```
InteriorPointCentralityCondition{CO,R}
```

A functor to check the centrality condition.

In order to obtain a step in the linesearch performed within the [`interior_point_Newton`](@ref), Section 6 of [LaiYoshise:2024](@cite) propose the following additional conditions to hold inspired by the Euclidean case described in Section 6 [El-BakryTapiaTsuchiyaZhang:1996](@cite):

For a given [`ConstrainedManifoldObjective`](@ref) assume consider the [`KKTVectorField`](@ref) $F$, that is we are at a point $q = (p, λ, μ, s)$  on $\mathcal M × ℝ^m × ℝ^n × ℝ^m$and a search direction $V = (X, Y, Z, W)$.

Then, let

$$
τ_1 = \frac{m⋅\min\{ μ ⊙ s\}}{μ^{\mathrm{T}}s}
\quad\text{ and }\quad
τ_2 = \frac{μ^{\mathrm{T}}s}{\lVert F(q) \rVert}
$$

where $⊙$ denotes the Hadamard (or elementwise) product.

For a new candidate $q(α) = \bigl(p(α), λ(α), μ(α), s(α)\bigr) := (\operatorname{retr}_p(αX), λ+αY, μ+αZ, s+αW)$, we then define two functions

$$
c_1(α) = \min\{ μ(α) ⊙ s(α) \} - \frac{γτ_1 μ(α)^{\mathrm{T}}s(α)}{m}
\quad\text{ and }\quad
c_2(α) = μ(α)^{\mathrm{T}}s(α) – γτ_2 \lVert F(q(α)) \rVert.
$$

While the paper now states that the (Armijo) linesearch starts at a point $\tilde α$, it is easier to include the condition that $c_1(α) ≥ 0$ and $c_2(α) ≥ 0$ into the linesearch as well.

The functor `InteriorPointCentralityCondition(cmo, γ, μ, s, normKKT)(N,qα)` defined here evaluates this condition and returns true if both $c_1$ and $c_2$ are nonnegative.

# Fields

  * `cmo`: a [`ConstrainedManifoldObjective`](@ref)
  * `γ`: a constant
  * `τ1`, `τ2`: the constants given in the formula.

# Constructor

```
InteriorPointCentralityCondition(cmo, γ)
InteriorPointCentralityCondition(cmo, γ, τ1, τ2)
```

Initialise the centrality conditions. The parameters `τ1`, `τ2` are initialise to zero if not provided.

!!! note
    Besides [`get_parameter`](@ref) for all three constants, and [`set_parameter!`](@ref) for $γ$, to update $τ_1$ and $τ_2$, call `set_parameter(ipcc, :τ, N, q)` to update both $τ_1$ and $τ_2$ according to the formulae above.

