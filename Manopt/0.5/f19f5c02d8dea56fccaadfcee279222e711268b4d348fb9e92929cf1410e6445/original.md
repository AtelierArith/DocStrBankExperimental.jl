```
LevenbergMarquardt(M, f, jacobian_f, p, num_components=-1; kwargs...)
LevenbergMarquardt(M, vgf, p; kwargs...)
LevenbergMarquardt(M, nlso, p; kwargs...)
LevenbergMarquardt!(M, f, jacobian_f, p, num_components=-1; kwargs...)
LevenbergMarquardt!(M, vgf, p, num_components=-1; kwargs...)
LevenbergMarquardt!(M, nlso, p, num_components=-1; kwargs...)
```

compute the the Riemannian Levenberg-Marquardt algorithm [Peeters:1993, AdachiOkunoTakeda:2022](@cite) to solve

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} \frac{1}{2} \sum_{i=1}^m \lvert f_i(p) \rvert^2
$$

where $f: \mathcal M → ℝ^m$ is written with component functions $f_i: \mathcal M → ℝ$, $i=1,…,m$, and each component function is continuously differentiable.

The second block of signatures perform the optimization in-place of `p`.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ℝ^m$. The cost function can be provided in two different ways

      * as a single function returning a vector $f(p) ∈ ℝ^m$
      * as a vector of functions, where each single function returns a scalar $f_i(p) ∈ ℝ$

    The type is determined by the `function_type=` keyword argument.
  * `jacobian_f`:   the Jacobian of $f$. The Jacobian can be provided in three different ways

      * as a single function returning a vector of gradient vectors $\bigl(\operatorname{grad} f_i(p)\bigr)_{i=1}^m$
      * as a vector of functions, where each single function returns a gradient vector $\operatorname{grad} f_i(p)$, $i=1,…,m$
      * as a single function returning a (coefficient) matrix $J ∈ ℝ^{m×d}$, where $d$ is the dimension of the manifold.

    These coefficients are given with respect to an [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) of the tangent space at `p`. The type is determined by the `jacobian_type=` keyword argument.
  * `p`: a point on the manifold $\mathcal M$
  * `num_components`: length $m$ of the vector returned by the cost function. By default its value is -1 which means that it is determined automatically by calling `f` one additional time. This is only possible when `evaluation` is [`AllocatingEvaluation`](@ref), for mutating evaluation this value must be explicitly specified.

You can also provide the cost and its Jacobian already as a[`VectorGradientFunction`](@ref) `vgf`, Alternatively, passing a [`NonlinearLeastSquaresObjective`](@ref) `nlso`.

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `η=0.2`:                   scaling factor for the sufficient cost decrease threshold required to accept new proposal points. Allowed range: `0 < η < 1`.
  * `expect_zero_residual=false`: whether or not the algorithm might expect that the value of residual (objective) at minimum is equal to 0.
  * `damping_term_min=0.1`:      initial (and also minimal) value of the damping term
  * `β=5.0`:                     parameter by which the damping term is multiplied when the current new point is rejected
  * `function_type=`[`FunctionVectorialType`](@ref): an [`AbstractVectorialType`](@ref) specifying the type of cost function provided.
  * `initial_jacobian_f`:      the initial Jacobian of the cost function `f`. By default this is a matrix of size `num_components` times the manifold dimension of similar type as `p`.
  * `initial_residual_values`: the initial residual vector of the cost function `f`. By default this is a vector of length `num_components` of similar type as `p`.
  * `jacobian_type=`[`FunctionVectorialType`](@ref): an [`AbstractVectorialType`](@ref) specifying the type of Jacobian provided.
  * `linear_subsolver!`:    a function with three arguments `sk, JJ, grad_f_c``that solves the linear subproblem`sk .= JJ \ grad*f*c`, where`JJ`is (up to numerical issues) a symmetric positive definite matrix. Default value is [`default*lm*lin_solve!`](@ref).
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
