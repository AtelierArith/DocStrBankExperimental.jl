```
stochastic_gradient_descent(M, grad_f, p; kwargs...)
stochastic_gradient_descent(M, msgo, p; kwargs...)
```

perform a stochastic gradient descent

# Input

  * `M`:      a manifold $\mathcal M$
  * `grad_f`: a gradient function, that either returns a vector of the subgradients or is a vector of gradients
  * `p`:      an initial value $x ∈ \mathcal M$

alternatively to the gradient you can provide an [`ManifoldStochasticGradientObjective`](@ref) `msgo`, then using the `cost=` keyword does not have any effect since if so, the cost is already within the objective.

# Optional

  * `cost`:               (`missing`) you can provide a cost function for example to track the function value
  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) specify whether the gradients works by  allocation (default) form `gradF(M, x)` or [`InplaceEvaluation`](@ref) in place of the form `gradF!(M, X, x)` (elementwise).
  * `evaluation_order`:   (`:Random`) specify whether to use a randomly permuted sequence (`:FixedRandom`), a per cycle permuted sequence (`:Linear`) or the default `:Random` one.
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(1000)`) a [`StoppingCriterion`](@ref)
  * `stepsize`:           ([`ConstantStepsize`](@ref)`(1.0)`) a [`Stepsize`](@ref)
  * `order_type`:         (`:RandomOder`) a type of ordering of gradient evaluations. Possible values are `:RandomOrder`, a `:FixedPermutation`, `:LinearOrder`
  * `order`:              (`[1:n]`) the initial permutation, where `n` is the number of gradients in `gradF`.
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) a retraction to use.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
