```
difference_of_convex_proximal_point(M, grad_h, p=rand(M); kwargs...)
difference_of_convex_proximal_point(M, mdcpo, p=rand(M); kwargs...)
difference_of_convex_proximal_point!(M, grad_h, p; kwargs...)
difference_of_convex_proximal_point!(M, mdcpo, p; kwargs...)
```

Compute the difference of convex proximal point algorithm [SouzaOliveira:2015](@cite) to minimize

$$
    \operatorname*{arg\,min}_{p∈\mathcal M} g(p) - h(p)
$$

where you have to provide the subgradient $∂h$ of $h$ and either

  * the proximal map $\operatorname{prox}_{λg}$ of `g` as a function `prox_g(M, λ, p)` or  `prox_g(M, q, λ, p)`
  * the functions `g` and `grad_g` to compute the proximal map using a sub solver
  * your own sub-solver, specified by `sub_problem=`and `sub_state=`

This algorithm performs the following steps given a start point `p`= $p^{(0)}$. Then repeat for $k=0,1,…$

1. $X^{(k)}  ∈ \operatorname{grad} h(p^{(k)})$
2. $q^{(k)} = \operatorname{retr}_{p^{(k)}}(λ_kX^{(k)})$
3. $r^{(k)} = \operatorname{prox}_{λ_kg}(q^{(k)})$
4. $X^{(k)} = \operatorname{retr}^{-1}_{p^{(k)}}(r^{(k)})$
5. Compute a stepsize $s_k$ and
6. set $p^{(k+1)} = \operatorname{retr}_{p^{(k)}}(s_kX^{(k)})$.

until the `stopping_criterion` is fulfilled.

See [AlmeidaNetoOliveiraSouza:2020](@cite) for more details on the modified variant, where steps 4-6 are slightly changed, since here the classical proximal point method for DC functions is obtained for $s_k = 1$ and one can hence employ usual line search method.

# Keyword arguments

  * `λ`:                          ( `k -> 1/2` ) a function returning the sequence of prox parameters $λ_k$
  * `cost=nothing`: provide the cost `f`, for debug reasons / analysis
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `gradient=nothing`: specify $\operatorname{grad} f$, for debug / analysis  or enhancing the `stopping_criterion`
  * `prox_g=nothing`: specify a proximal map for the sub problem *or* both of the following
  * `g=nothing`: specify the function `g`.
  * `grad_g=nothing`: specify the gradient of `g`. If both `g`and `grad_g` are specified, a subsolver is automatically set up.
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`ConstantLength`](@ref)`()`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`): a functor indicating that the stopping criterion is fulfilled A [`StopWhenGradientNormLess`](@ref)`(1e-8)` is added with [`|`](@ref StopWhenAny), when a `gradient` is provided.
  * `sub_cost=`[`ProximalDCCost`](@ref)`(g, copy(M, p), λ(1))`): cost to be used within the default `sub_problem` that is initialized as soon as `g` is provided. This is used to define the `sub_objective=` keyword and has hence no effect, if you set `sub_objective` directly.
  * `sub_grad=`[`ProximalDCGrad`](@ref)`(grad_g, copy(M, p), λ(1); evaluation=evaluation)`: gradient to be used within the default `sub_problem`, that is initialized as soon as `grad_g` is provided. This is used to define the `sub_objective=` keyword and has hence no effect, if you set `sub_objective` directly.
  * `sub_hess`:              (a finite difference approximation using `sub_grad` by default):  specify a Hessian of the `sub_cost`, which the default solver, see `sub_state=` needs.
  * `sub_kwargs=``(;)`: a named tuple of keyword arguments that are passed to [`decorate_objective!`](@ref) of the sub solvers objective, the [`decorate_state!`](@ref) of the subsovlers state, and the sub state constructor itself.
  * `sub_objective`:         a gradient or Hessian objective based on `sub_cost=`, `sub_grad=`, and `sub_hess`if provided  the objective used within `sub_problem`. This is used to define the `sub_problem=` keyword and has hence no effect, if you set `sub_problem` directly.
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state=`([`GradientDescentState`](@ref) or [`TrustRegionsState`](@ref) if `sub_hessian` is provided):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `sub_stopping_criterion=`([`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)`[`StopWhenGradientNormLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled This is used to define the`sub*state=`keyword and has hence no effect, if you set`sub*state` directly.

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
