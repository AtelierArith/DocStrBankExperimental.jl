```
alternating_gradient_descent(M::ProductManifold, f, grad_f, p=rand(M))
alternating_gradient_descent(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
alternating_gradient_descent!(M::ProductManifold, f, grad_f, p)
alternating_gradient_descent!(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
```

perform an alternating gradient descent. This can be done in-place of the start point `p`

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: a gradient, that can be of two cases

      * is a single function returning an `ArrayPartition` from [`RecursiveArrayTools.jl`](https://docs.sciml.ai/RecursiveArrayTools/stable/array_types/) or
      * is a vector functions each returning a component part of the whole gradient
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `evaluation_order=:Linear`: whether to use a randomly permuted sequence (`:FixedRandom`), a per cycle permuted sequence (`:Random`) or the default `:Linear` one.
  * `inner_iterations=5`:  how many gradient steps to take in a component before alternating to the next
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`): a functor indicating that the stopping criterion is fulfilled
  * `stepsize=`[`ArmijoLinesearch`](@ref)`()`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `order=[1:n]`:         the initial permutation, where `n` is the number of gradients in `gradF`.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

# Output

usually the obtained (approximate) minimizer, see [`get_solver_return`](@ref) for details

!!! note
    The input of each of the (component) gradients is still the whole vector `X`, just that all other then the `i`th input component are assumed to be fixed and just the `i`th components gradient is computed / returned.

