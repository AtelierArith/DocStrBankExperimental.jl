```
alternating_gradient_descent(M::ProductManifold, f, grad_f, p=rand(M))
alternating_gradient_descent(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
```

perform an alternating gradient descent

# Input

  * `M`:      the product manifold $\mathcal M = \mathcal M_1 × \mathcal M_2 × ⋯ ×\mathcal M_n$
  * `f`:      the objective function (cost) defined on `M`.
  * `grad_f`: a gradient, that can be of two cases

      * is a single function returning an `ArrayPartition` or
      * is a vector functions each returning a component part of the whole gradient
  * `p`:      an initial value $p_0 ∈ \mathcal M$

# Optional

  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) specify whether the gradients work by allocation (default) form `gradF(M, x)` or [`InplaceEvaluation`](@ref) in place of the form `gradF!(M, X, x)` (elementwise).
  * `evaluation_order`:   (`:Linear`) whether to use a randomly permuted sequence (`:FixedRandom`), a per cycle permuted sequence (`:Random`) or the default `:Linear` one.
  * `inner_iterations`:   (`5`) how many gradient steps to take in a component before alternating to the next
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(1000)`) a [`StoppingCriterion`](@ref)
  * `stepsize`:           ([`ArmijoLinesearch`](@ref)`()`) a [`Stepsize`](@ref)
  * `order`:              (`[1:n]`) the initial permutation, where `n` is the number of gradients in `gradF`.
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) a `retraction(M, p, X)` to use.

# Output

usually the obtained (approximate) minimizer, see [`get_solver_return`](@ref) for details

!!! note
    The input of each of the (component) gradients is still the whole vector `X`, just that all other then the `i`th input component are assumed to be fixed and just the `i`th components gradient is computed / returned.

