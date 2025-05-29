```
AbstractVectorFunction{E, FT} <: Function
```

Represent an abstract vectorial function $f:\mathcal M → ℝ^n$ with an [`AbstractEvaluationType`](@ref) `E` and an [`AbstractVectorialType`](@ref) to specify the format $f$ is implemented as.

# Representations of $f$

There are three different representations of $f$, which might be beneficial in one or the other situation:

  * the [`FunctionVectorialType`](@ref),
  * the [`ComponentVectorialType`](@ref),
  * the [`CoordinateVectorialType`](@ref) with respect to a specific basis of the tangent space.

For the [`ComponentVectorialType`](@ref) imagine that $f$ could also be written using its component functions,

$$
f(p) = \bigl( f_1(p), f_2(p), \ldots, f_n(p) \bigr)^{\mathrm{T}}
$$

In this representation `f` is given as a vector `[f1(M,p), f2(M,p), ..., fn(M,p)]` of its component functions. An advantage is that the single components can be evaluated and from this representation one even can directly read of the number `n`. A disadvantage might be, that one has to implement a lot of individual (component) functions.

For the  [`FunctionVectorialType`](@ref) $f$ is implemented as a single function `f(M, p)`, that returns an `AbstractArray`. And advantage here is, that this is a single function. A disadvantage might be, that if this is expensive even to compute a single component, all of `f` has to be evaluated

For the [`ComponentVectorialType`](@ref) of `f`, each of the component functions is a (classical) objective.
