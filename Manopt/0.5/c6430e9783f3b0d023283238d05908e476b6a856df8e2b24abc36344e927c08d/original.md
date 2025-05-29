```
stochastic_gradient_descent(M, grad_f, p=rand(M); kwargs...)
stochastic_gradient_descent(M, msgo; kwargs...)
stochastic_gradient_descent!(M, grad_f, p; kwargs...)
stochastic_gradient_descent!(M, msgo, p; kwargs...)
```

perform a stochastic gradient descent. This can be perfomed in-place of `p`.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `grad_f`: a gradient function, that either returns a vector of the gradients or is a vector of gradient functions
  * `p`: a point on the manifold $\mathcal M$

alternatively to the gradient you can provide an [`ManifoldStochasticGradientObjective`](@ref) `msgo`, then using the `cost=` keyword does not have any effect since if so, the cost is already within the objective.

# Keyword arguments

  * `cost=missing`: you can provide a cost function for example to track the function value
  * `direction=`[`StochasticGradient`](@ref)`([`zero*vector`](@extref`ManifoldsBase.zero*vector-Tuple{AbstractManifold, Any}`)`(M, p)`)
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `evaluation_order=:Random`: specify whether to use a randomly permuted sequence (`:FixedRandom`:, a per cycle permuted sequence (`:Linear`) or the default `:Random` one.
  * `order_type=:RandomOder`: a type of ordering of gradient evaluations. Possible values are `:RandomOrder`, a `:FixedPermutation`, `:LinearOrder`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`: a functor indicating that the stopping criterion is fulfilled
  * `stepsize=`[`default_stepsize`](@ref)`(M, StochasticGradientDescentState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `order=[1:n]`: the initial permutation, where `n` is the number of gradients in `gradF`.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
