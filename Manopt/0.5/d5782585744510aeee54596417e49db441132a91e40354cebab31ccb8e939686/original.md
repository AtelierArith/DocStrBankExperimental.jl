```
adaptive_regularization_with_cubics(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, f, grad_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, mho, p=rand(M); kwargs...)
adaptive_regularization_with_cubics!(M, f, grad_f, Hess_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, f, grad_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, mho, p; kwargs...)
```

Solve an optimization problem on the manifold `M` by iteratively minimizing

$$
m_k(X) = f(p_k) + ⟨X, \operatorname{grad} f(p^{(k)})⟩ + \frac{1}{2}⟨X, \operatorname{Hess} f(p^{(k)})[X]⟩ + \frac{σ_k}{3}\lVert X \rVert^3
$$

on the tangent space at the current iterate $p_k$, where $X ∈ T_{p_k}\mathcal M$ and $σ_k > 0$ is a regularization parameter.

Let $Xp^{(k)}$ denote the minimizer of the model $m_k$ and use the model improvement

$$
  ρ_k = \frac{f(p_k) - f(\operatorname{retr}_{p_k}(X_k))}{m_k(0) - m_k(X_k) + \frac{σ_k}{3}\lVert X_k\rVert^3}.
$$

With two thresholds $η_2 ≥ η_1 > 0$ set $p_{k+1} = \operatorname{retr}_{p_k}(X_k)$ if $ρ ≥ η_1$ and reject the candidate otherwise, that is, set $p_{k+1} = p_k$.

Further update the regularization parameter using factors $0 < γ_1 < 1 < γ_2$ reads

$$
σ_{k+1} =
\begin{cases}
    \max\{σ_{\min}, γ_1σ_k\} & \text{ if } ρ \geq η_2 &\text{   (the model was very successful)},\\
    σ_k & \text{ if } ρ ∈ [η_1, η_2)&\text{   (the model was successful)},\\
    γ_2σ_k & \text{ if } ρ < η_1&\text{   (the model was unsuccessful)}.
\end{cases}
$$

For more details see [AgarwalBoumalBullinsCartis:2020](@cite).

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `Hess_f`: the (Riemannian) Hessian $\operatorname{Hess}f: T_{p}\mathcal M → T_{p}\mathcal M$ of f as a function `(M, p, X) -> Y` or a function `(M, Y, p, X) -> Y` computing `Y` in-place
  * `p`: a point on the manifold $\mathcal M$

the cost `f` and its gradient and Hessian might also be provided as a [`ManifoldHessianObjective`](@ref)

# Keyword arguments

  * `σ=100.0 / sqrt(manifold_dimension(M)`: initial regularization parameter
  * `σmin=1e-10`: minimal regularization value $σ_{\min}$
  * `η1=0.1`: lower model success threshold
  * `η2=0.9`: upper model success threshold
  * `γ1=0.1`: regularization reduction factor (for the success case)
  * `γ2=2.0`: regularization increment factor (for the non-success case)
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `initial_tangent_vector=zero_vector(M, p)`: initialize any tangent vector data,
  * `maxIterLanczos=200`: a shortcut to set the stopping criterion in the sub solver,
  * `ρ_regularization=1e3`: a regularization to avoid dividing by zero for small values of cost and model
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`):
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(40)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-9)`[`|`](@ref StopWhenAny)[`StopWhenAllLanczosVectorsUsed`](@ref)`(maxIterLanczos)`: a functor indicating that the stopping criterion is fulfilled
  * `sub_kwargs=``(;)`: a named tuple of keyword arguments that are passed to [`decorate_objective!`](@ref) of the sub solvers objective, the [`decorate_state!`](@ref) of the subsovlers state, and the sub state constructor itself.
  * `sub_objective=nothing`: a shortcut to modify the objective of the subproblem used within in the `sub_problem=` keyword By default, this is initialized as a [`AdaptiveRagularizationWithCubicsModelObjective`](@ref), which can further be decorated by using the `sub_kwargs=` keyword.
  * `sub_state=`[`LanczosState`](@ref)`(M, copy(M,p))`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

If you provide the [`ManifoldGradientObjective`](@ref) directly, the `evaluation=` keyword is ignored. The decorations are still applied to the objective.

If you activate tutorial mode (cf. [`is_tutorial_mode`](@ref)), this solver provides additional debug warnings.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
