```
ManifoldConstrainedSetObjective{E, MO, PF, IF} <: AbstractManifoldObjective{E}
```

Model a constrained objective restricted to a set

$$
\operatorname*{arg\,min}_{p ∈ \mathcal C} f(p)
$$

where $\mathcal C ⊂ \mathcal M$ is a convex closed subset.

# Fields

  * `objective::AbstractManifoldObjective` the (unconstrained) objective, which contains $f$ and for example ist gradient $\operatorname{grad} f$.
  * `project!!::PF` a projection function $\operatorname{proj}_{\mathcal C}: \mathcal M → \mathcal C$ that projects onto the set $\mathcal C$.
  * `indicator::IF` the indicator function ``ι_{\mathcal C}(p) = \begin{cases}   0 &\text{ for }p∈\mathcal C\\    ∞ &\text{ else.}\end{cases}

# Constructor

```
ManifoldConstrainedSetObjective(f, grad_f, project!!; kwargs...)
```

Generate the constrained objective for a given function `f` its gradient `grad_f` and a projection `project!!` $\operatorname{proj}_{\mathcal C}$.

## Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `indicator=nothing`: the indicator function $ι_{\mathcal C}(p)$. If not provided a test, whether the projection yields the same point is performed. For the [`InplaceEvaluation`](@ref) this required one allocation.
