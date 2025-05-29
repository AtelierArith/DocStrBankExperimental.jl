```
ConjugateGradientBealeRestart(direction_update::Union{DirectionUpdateRule,ManifoldDefaultsFactory}; kwargs...)
ConjugateGradientBealeRestart(M::AbstractManifold, direction_update::Union{DirectionUpdateRule,ManifoldDefaultsFactory}; kwargs...)
```

Compute a conjugate gradient coefficient with a potential restart, when two directions are nearly orthogonal. See [HagerZhang:2006; page 12](@cite) (in the preprint, page 46 in Journal page numbers). This method is named after E. Beale from his proceedings paper in 1972 [Beale:1972](@cite). This method acts as a *decorator* to any existing [`DirectionUpdateRule`](@ref) `direction_update`.

Denote the last iterate and gradient by $p_k,X_k$, the current iterate and gradient by $p_{k+1}, X_{k+1}$, respectively, as well as the last update direction by $δ_k$.

Then a restart is performed, hence $β_k = 0$ returned if

$$
  \frac{⟨X_{k+1}, \mathcal T_{p_{k+1}←p_k}X_k⟩}{\lVert X_k \rVert_{p_k}} > ε,
$$

where $ε$ is the `threshold`, which is set by default to `0.2`, see [Powell:1977](@cite)

## Input

  * `direction_update`: a [`DirectionUpdateRule`](@ref) or a corresponding [`ManifoldDefaultsFactory`](@ref) to produce such a rule.

## Keyword arguments

  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `threshold=0.2`

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`ConjugateGradientBealeRestartRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

