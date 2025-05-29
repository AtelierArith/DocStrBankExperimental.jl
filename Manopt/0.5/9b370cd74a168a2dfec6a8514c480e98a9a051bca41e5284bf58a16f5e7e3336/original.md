```
VectorHessianFunction{E, FT, JT, HT, F, J, H, I} <: AbstractVectorGradientFunction{E, FT, JT}
```

Represent a function $f:\mathcal M M → ℝ^n$ including it first derivative, either as a vector of gradients of a Jacobian, and the Hessian, as a vector of Hessians of the component functions.

Both the Jacobian and the Hessian can map into either a sequence of tangent spaces or a single tangent space of the power manifold of length `n`.

# Fields

  * `value!!::F`:          the cost function $f$, which can take different formats
  * `cost_type::`[`AbstractVectorialType`](@ref):     indicating / string data for the type of `f`
  * `jacobian!!::G`:     the Jacobian $J_f$ of $f$
  * `jacobian_type::`[`AbstractVectorialType`](@ref): indicating / storing data for the type of $J_f$
  * `hessians!!::H`:     the Hessians of $f$ (in a component wise sense)
  * `hessian_type::`[`AbstractVectorialType`](@ref):  indicating / storing data for the type of $H_f$
  * `range_dimension`:    the number `n` from, the size of the vector $f$ returns.

# Constructor

```
VectorHessianFunction(f, Jf, Hess_f, range_dimension;
    evaluation::AbstractEvaluationType=AllocatingEvaluation(),
    function_type::AbstractVectorialType=FunctionVectorialType(),
    jacobian_type::AbstractVectorialType=FunctionVectorialType(),
    hessian_type::AbstractVectorialType=FunctionVectorialType(),
)
```

Create a `VectorHessianFunction` of `f`  and its Jacobian (vector of gradients) `Jf` and (vector of) Hessians, where `f` maps into the Euclidean space of dimension `range_dimension`. Their types are specified by the `function_type`, and `jacobian_type`, and `hessian_type`, respectively. The Jacobian and Hessian can further be given as an allocating variant or an inplace-variant, specified by the `evaluation=` keyword.
