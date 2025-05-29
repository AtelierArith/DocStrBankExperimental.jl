```
ManifoldDifferenceOfConvexObjective{E} <: AbstractManifoldCostObjective{E}
```

Specify an objective for a [`difference_of_convex_algorithm`](@ref).

The objective $f: \mathcal M → ℝ$ is given as

$$
    f(p) = g(p) - h(p)
$$

where both $g$ and $h$ are convex, lower semicontinuous and proper. Furthermore the subdifferential $∂h$ of $h$ is required.

# Fields

  * `cost`: an implementation of $f(p) = g(p)-h(p)$ as a function `f(M,p)`.
  * `∂h!!`: a deterministic version of $∂h: \mathcal M → T\mathcal M$, in the sense that calling `∂h(M, p)` returns a subgradient of $h$ at `p` and if there is more than one, it returns a deterministic choice.

Note that the subdifferential might be given in two possible signatures

  * `∂h(M,p)` which does an [`AllocatingEvaluation`](@ref)
  * `∂h!(M, X, p)` which does an [`InplaceEvaluation`](@ref) in place of `X`.
