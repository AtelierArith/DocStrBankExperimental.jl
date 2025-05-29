```
AbstractManifoldObjective{E<:AbstractEvaluationType}
```

Describe the collection of the optimization function $f: \mathcal M → ℝ$ (or even a vectorial range) and its corresponding elements, which might for example be a gradient or (one or more) proximal maps.

All these elements should usually be implemented as functions `(M, p) -> ...`, or `(M, X, p) -> ...` that is

  * the first argument of these functions should be the manifold `M` they are defined on
  * the argument `X` is present, if the computation is performed in-place of `X` (see [`InplaceEvaluation`](@ref))
  * the argument `p` is the place the function ($f$ or one of its elements) is evaluated **at**.

the type `T` indicates the global [`AbstractEvaluationType`](@ref).
