```
VectorGradientFunction{E, FT, JT, F, J, I} <: AbstractManifoldObjective{E}
```

Represent an abstract vectorial function $f:\mathcal M → ℝ^n$ that provides a (component wise) gradient. The [`AbstractEvaluationType`](@ref) `E` indicates the evaluation type, and the [`AbstractVectorialType`](@ref)s `FT` and `JT` the formats in which the function and the gradient are provided, see [`AbstractVectorFunction`](@ref) for an explanation.
