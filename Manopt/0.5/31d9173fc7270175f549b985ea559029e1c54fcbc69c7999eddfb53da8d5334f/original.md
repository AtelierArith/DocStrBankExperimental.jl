```
difference_of_convex_algorithm(M, f, g, ∂h, p=rand(M); kwargs...)
difference_of_convex_algorithm(M, mdco, p; kwargs...)
difference_of_convex_algorithm!(M, f, g, ∂h, p; kwargs...)
difference_of_convex_algorithm!(M, mdco, p; kwargs...)
```

Compute the difference of convex algorithm [BergmannFerreiraSantosSouza:2024](@cite) to minimize

$$
    \operatorname*{arg\,min}_{p∈\mathcal M}\ g(p) - h(p)
$$

where you need to provide $f(p) = g(p) - h(p)$, $g$ and the subdifferential $∂h$ of $h$.

This algorithm performs the following steps given a start point `p`= $p^{(0)}$. Then repeat for $k=0,1,…$

1. Take $X^{(k)}  ∈ ∂h(p^{(k)})$
2. Set the next iterate to the solution of the subproblem

$$
  p^{(k+1)} ∈ \operatorname*{arg\,min}_{q ∈ \mathcal M} g(q) - ⟨X^{(k)}, \log_{p^{(k)}}q⟩
$$

until the stopping criterion (see the `stopping_criterion` keyword is fulfilled.

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `gradient=nothing`:        specify $\operatorname{grad} f$, for debug / analysis or enhancing the `stopping_criterion=`
  * `grad_g=nothing`:          specify the gradient of `g`. If specified, a subsolver is automatically set up.
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled
  * `g=nothing`:               specify the function `g` If specified, a subsolver is automatically set up.
  * `sub_cost=`[`LinearizedDCCost`](@ref)`(g, p, initial_vector)`: a cost to be used within the default `sub_problem`. This is used to define the `sub_objective=` keyword and has hence no effect, if you set `sub_objective` directly.
  * `sub_grad=`[`LinearizedDCGrad`](@ref)`(grad_g, p, initial_vector; evaluation=evaluation)`: gradient to be used within the default `sub_problem`. This is used to define the `sub_objective=` keyword and has hence no effect, if you set `sub_objective` directly.
  * `sub_hess`:              (a finite difference approximation using `sub_grad` by default):  specify a Hessian of the `sub_cost`, which the default solver, see `sub_state=` needs. This is used to define the `sub_objective=` keyword and has hence no effect, if you set `sub_objective` directly.
  * `sub_kwargs=``(;)`: a named tuple of keyword arguments that are passed to [`decorate_objective!`](@ref) of the sub solvers objective, the [`decorate_state!`](@ref) of the subsovlers state, and the sub state constructor itself.
  * `sub_objective`:         a gradient or Hessian objective based on `sub_cost=`, `sub_grad=`, and `sub_hess`if provided  the objective used within `sub_problem`. This is used to define the `sub_problem=` keyword and has hence no effect, if you set `sub_problem` directly.
  * `sub_state=`([`GradientDescentState`](@ref) or [`TrustRegionsState`](@ref) if `sub_hessian` is provided):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-9)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-9)`: a stopping criterion used withing the default `sub_state=` This is used to define the `sub_state=` keyword and has hence no effect, if you set `sub_state` directly.
  * `sub_stepsize=`[`ArmijoLinesearch`](@ref)`(M)`) specify a step size used within the `sub_state`. This is used to define the `sub_state=` keyword and has hence no effect, if you set `sub_state` directly.
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
