```
Polyak(; kwargs...)
Polyak(M::AbstractManifold; kwargs...)
```

Compute a step size according to a method propsed by Polyak, cf. the Dynamic step size discussed in Section 3.2 of [Bertsekas:2015](@cite). This has been generalised here to both the Riemannian case and to approximate the minimum cost value.

Let $f_{\text{best}$ be the best cost value seen until now during some iterative optimisation algorithm and let $γ_k$ be a sequence of numbers that is square summable, but not summable.

Then the step size computed here reads

$$
s_k = \frac{f(p^{(k)}) - f_{\text{best} + γ_k}{\lVert ∂f(p^{(k)})} \rVert_{}},
$$

where $∂f$ denotes a nonzero-subgradient of $f$ at the current iterate $p^{(k)}$.

# Constructor

```
Polyak(; γ = k -> 1/k, initial_cost_estimate=0.0)
```

initialize the Polyak stepsize to a certain sequence and an initial estimate of $f_{	ext{best}}$.

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`PolyakStepsize`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

