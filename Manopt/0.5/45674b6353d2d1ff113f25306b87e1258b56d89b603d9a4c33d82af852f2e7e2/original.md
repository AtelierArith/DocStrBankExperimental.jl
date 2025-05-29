```
VectorGradientFunction{E, FT, JT, F, J, I} <: AbstractVectorGradientFunction{E, FT, JT}
```

Represent a function $f:\mathcal M → ℝ^n$ including it first derivative, either as a vector of gradients of a Jacobian

And hence has a gradient ``\operatorname{grad} f_i(p) ∈ T_{p}\mathcal M`. Putting these gradients into a vector the same way as the functions, yields a [`ComponentVectorialType`](@ref)

$$
\operatorname{grad} f(p) = \Bigl( \operatorname{grad} f_1(p), \operatorname{grad} f_2(p), …, \operatorname{grad} f_n(p) \Bigr)^\mathrm{T}
∈ (T_{p}\mathcal M)^n
$$

And advantage here is, that again the single components can be evaluated individually

# Fields

  * `value!!::F`:          the cost function $f$, which can take different formats
  * `cost_type::`[`AbstractVectorialType`](@ref):     indicating / storing data for the type of `f`
  * `jacobian!!::G`:     the Jacobian of $f$
  * `jacobian_type::`[`AbstractVectorialType`](@ref): indicating / storing data for the type of $J_f$
  * `parameters`:    the number `n` from, the size of the vector $f$ returns.

# Constructor

```
VectorGradientFunction(f, Jf, range_dimension;
    evaluation::AbstractEvaluationType=AllocatingEvaluation(),
    function_type::AbstractVectorialType=FunctionVectorialType(),
    jacobian_type::AbstractVectorialType=FunctionVectorialType(),
)
```

Create a `VectorGradientFunction` of `f`  and its Jacobian (vector of gradients) `Jf`, where `f` maps into the Euclidean space of dimension `range_dimension`. Their types are specified by the `function_type`, and `jacobian_type`, respectively. The Jacobian can further be given as an allocating variant or an in-place variant, specified by the `evaluation=` keyword.
