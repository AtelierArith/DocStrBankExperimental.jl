```
Frank_Wolfe_method(M, f, grad_f, p=rand(M))
Frank_Wolfe_method(M, gradient_objective, p=rand(M); kwargs...)
Frank_Wolfe_method!(M, f, grad_f, p; kwargs...)
Frank_Wolfe_method!(M, gradient_objective, p; kwargs...)
```

Perform the Frank-Wolfe algorithm to compute for $\mathcal C ⊂ \mathcal M$ the constrained problem

$$
    \operatorname*{arg\,min}_{p∈\mathcal C} f(p),
$$

where the main step is a constrained optimisation is within the algorithm, that is the sub problem (Oracle)

$$
   \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

for every iterate $p_k$ together with a stepsize $s_k≤1$. The algorhtm can be performed in-place of `p`.

This algorithm is inspired by but slightly more general than [WeberSra:2022](@cite).

The next iterate is then given by $p_{k+1} = γ_{p_k,q_k}(s_k)$, where by default $γ$ is the shortest geodesic between the two points but can also be changed to use a retraction and its inverse.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `p`: a point on the manifold $\mathcal M$

Alternatively to `f` and `grad_f` you can provide the corresponding [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`DecreasingStepsize`](@ref)`(; length=2.0, shift=2)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`): a functor indicating that the stopping criterion is fulfilled
  * `sub_cost=`[`FrankWolfeCost`](@ref)`(p, X)`: the cost of the Frank-Wolfe sub problem. This is used to define the `sub_objective=` keyword and has hence no effect, if you set `sub_objective` directly.
  * `sub_grad=`[`FrankWolfeGradient`](@ref)`(p, X)`: the gradient of the Frank-Wolfe sub problem. This is used to define the `sub_objective=` keyword and has hence no effect, if you set `sub_objective` directly.
  * `sub_kwargs=``(;)`: a named tuple of keyword arguments that are passed to [`decorate_objective!`](@ref) of the sub solvers objective, the [`decorate_state!`](@ref) of the subsovlers state, and the sub state constructor itself.
  * `sub_objective=`[`ManifoldGradientObjective`](@ref)`(sub_cost, sub_gradient)`: the objective for the Frank-Wolfe sub problem. This is used to define the `sub_problem=` keyword and has hence no effect, if you set `sub_problem` directly.
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state=`[`GradientDescentState`](@ref)`(M, copy(M,p))`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate
  * `sub_stopping_criterion=``[`StopAfterIteration`](@ref)`(300)`[` | `](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled This is used to define the`sub*state=`keyword and has hence no effect, if you set`sub*state` directly.
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

If you provide the [`ManifoldGradientObjective`](@ref) directly, the `evaluation=` keyword is ignored. The decorations are still applied to the objective.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
