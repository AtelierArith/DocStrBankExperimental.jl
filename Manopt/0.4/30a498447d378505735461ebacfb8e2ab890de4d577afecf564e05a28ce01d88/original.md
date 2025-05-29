```
Frank_Wolfe_method(M, f, grad_f, p)
Frank_Wolfe_method(M, gradient_objective, p; kwargs...)
```

Perform the Frank-Wolfe algorithm to compute for $\mathcal C \subset \mathcal M$

$$
    \operatorname*{arg\,min}_{p∈\mathcal C} f(p),
$$

where the main step is a constrained optimisation is within the algorithm, that is the sub problem (Oracle)

$$
    q_k = \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

for every iterate $p_k$ together with a stepsize $s_k≤1$, by default $s_k = \frac{2}{k+2}$. This algorithm is inspired by but slightly more general than [WeberSra:2022](@cite).

The next iterate is then given by $p_{k+1} = γ_{p_k,q_k}(s_k)$, where by default $γ$ is the shortest geodesic between the two points but can also be changed to use a retraction and its inverse.

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $f: \mathcal M→ℝ$ to find a minimizer $p^*$ for
  * `grad_f`: the gradient $\operatorname{grad}f: \mathcal M → T\mathcal M$ of f
  * `p`:      an initial value $p ∈ \mathcal C$, note that it really has to be a feasible point

Alternatively to `f` and `grad_f` you can provide the [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` directly.

# Keyword arguments

  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) whether `grad_f` is an in-place or allocating (default) function
  * `initial_vector`:     (`zero_vectoir(M,p)`) how to initialize the inner gradient tangent vector
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(500) |`[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`) a stopping criterion
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) a type of retraction
  * `stepsize`:           ([`DecreasingStepsize`](@ref)`(; length=2.0, shift=2)` a [`Stepsize`](@ref) to use; it has to be always less than 1. The default is the one proposed by Frank & Wolfe: $s_k = \frac{2}{k+2}$.
  * `sub_cost`:           ([`FrankWolfeCost`](@ref)`(p, initiel_vector)`) the cost of the Frank-Wolfe sub problem which by default uses the current iterate and (sub)gradient of the current iteration to define a default cost, this is used to define the default `sub_objective`. It is ignored, if you set that or the `sub_problem` directly
  * `sub_grad`:           ([`FrankWolfeGradient`](@ref)`(p, initial_vector)`) the gradient of the Frank-Wolfe sub problem which by default uses the current iterate and (sub)gradient of the current iteration to define a default gradient this is used to define the default `sub_objective`. It is ignored, if you set that or the `sub_problem` directly
  * `sub_objective`:      ([`ManifoldGradientObjective`](@ref)`(sub_cost, sub_gradient)`) the objective for the Frank-Wolfe sub problem this is used to define the default `sub_problem`. It is ignored, if you set the `sub_problem` manually
  * `sub_problem`:        ([`DefaultManoptProblem`](@ref)`(M, sub_objective)`) the Frank-Wolfe sub problem to solve. This can be given in three forms

    1. as an [`AbstractManoptProblem`](@ref), then the `sub_state` specifies the solver to use
    2. as a closed form solution, as a function evaluating with new allocations `(M, p, X) -> q` that solves the sub problem on `M` given the current iterate `p` and (sub)gradient `X`.
    3. as a closed form solution, as a function `(M, q, p, X) -> q` working in place of `q`.

    For points 2 and 3 the `sub_state` has to be set to the corresponding [`AbstractEvaluationType`](@ref), [`AllocatingEvaluation`](@ref) and [`InplaceEvaluation`](@ref), respectively
  * `sub_state`:          (`evaluation` if `sub_problem` is a function, a decorated [`GradientDescentState`](@ref) otherwise) for a function, the evaluation is inherited from the Frank-Wolfe `evaluation` keyword.
  * `sub_kwargs`:         (`(;)`) keyword arguments to decorate the `sub_state` default state in case the `sub_problem` is not a function

All other keyword arguments are passed to [`decorate_state!`](@ref) for decorators or [`decorate_objective!`](@ref), respectively. If you provide the [`ManifoldGradientObjective`](@ref) directly, these decorations can still be specified

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
