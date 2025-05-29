```
NonlinearLeastSquaresObjective{E<:AbstractEvaluationType} <: AbstractManifoldObjective{T}
```

An objective to model the nonlinear least squares problem

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} \frac{1}{2} \sum_{i=1}^m \lvert f_i(p) \rvert^2
$$

where $f: \mathcal M → ℝ^m$ is written with component functions $f_i: \mathcal M → ℝ$, $i=1,…,m$, and each component function is continuously differentiable.

Specify a nonlinear least squares problem

# Fields

  * `objective`: a [`AbstractVectorGradientFunction`](@ref)`{E}` containing both the vector of cost functions $f_i$ (or a function returning a vector of costs) as well as their gradients $\operatorname{grad} f_i$ (or Jacobian of the vector-valued function).

This `NonlinearLeastSquaresObjective` then has the same [`AbstractEvaluationType`](@ref) `T` as the (inner) `objective`.

# Constructors

```
NonlinearLeastSquaresObjective(f, jacobian, range_dimension::Integer; kwargs...)
NonlinearLeastSquaresObjective(vf::AbstractVectorGradientFunction)
```

# Arguments

  * `f` the vectorial cost function $f: \mathcal M → ℝ^m$
  * `jacobian` the Jacobian, might also be a vector of gradients of the component functions of `f`
  * `range_dimension::Integer` the number of dimensions `m` the function `f` maps into

These three can also be passed as a [`AbstractVectorGradientFunction`](@ref) `vf` already.

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `function_type::`[`AbstractVectorialType`](@ref)`=`[`FunctionVectorialType`](@ref)`()`: specify the format the residuals are given in. By default a function returning a vector.
  * `jacobian_tangent_basis::AbstractBasis=DefaultOrthonormalBasis()`; shortcut to specify the basis the Jacobian matrix is build with.
  * `jacobian_type::`[`AbstractVectorialType`](@ref)`=`[`CoordinateVectorialType`](@ref)`(jacobian_tangent_basis)`: specify the format the Jacobian is given in. By default a matrix of the differential with respect to a certain basis of the tangent space.

# See also

[`LevenbergMarquardt`](@ref), [`LevenbergMarquardtState`](@ref)
