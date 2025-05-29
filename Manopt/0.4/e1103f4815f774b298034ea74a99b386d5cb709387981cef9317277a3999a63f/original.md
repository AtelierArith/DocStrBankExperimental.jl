```
adaptive_regularization_with_cubics(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, f, grad_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, mho, p=rand(M); kwargs...)
```

Solve an optimization problem on the manifold `M` by iteratively minimizing

$$
  m_k(X) = f(p_k) + ⟨X, \operatorname{grad} f(p_k)⟩ + \frac{1}{2}⟨X, \operatorname{Hess} f(p_k)[X]⟩ + \frac{σ_k}{3}\lVert X \rVert^3
$$

on the tangent space at the current iterate $p_k$, where $X ∈ T_{p_k}\mathcal M$ and $σ_k > 0$ is a regularization parameter.

Let $X_k$ denote the minimizer of the model $m_k$ and use the model improvement

$$
  ρ_k = \frac{f(p_k) - f(\operatorname{retr}_{p_k}(X_k))}{m_k(0) - m_k(X_k) + \frac{σ_k}{3}\lVert X_k\rVert^3}.
$$

With two thresholds $η_2 ≥ η_1 > 0$ set $p_{k+1} = \operatorname{retr}_{p_k}(X_k)$ if $ρ ≥ η_1$ and reject the candidate otherwise, that is, set $p_{k+1} = p_k$.

Further update the regularization parameter using factors $0 < γ_1 < 1 < γ_2$

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

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $F: \mathcal M → ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad}F: \mathcal M → T \mathcal M$ of $F$
  * `Hess_f`: (optional) the Hessian $H( \mathcal M, x, ξ)$ of $F$
  * `p`:      an initial value $p ∈ \mathcal M$

For the case that no Hessian is provided, the Hessian is computed using finite difference, see [`ApproxHessianFiniteDifference`](@ref).

the cost `f` and its gradient and Hessian might also be provided as a [`ManifoldHessianObjective`](@ref)

# Keyword arguments

the default values are given in brackets

  * `σ`:                      (`100.0 / sqrt(manifold_dimension(M)`) initial regularization parameter
  * `σmin`:                   (`1e-10`) minimal regularization value $σ_{\min}$
  * `η1`:                     (`0.1`) lower model success threshold
  * `η2`:                     (`0.9`) upper model success threshold
  * `γ1`:                     (`0.1`) regularization reduction factor (for the success case)
  * `γ2`:                     (`2.0`) regularization increment factor (for the non-success case)
  * `evaluation`:             ([`AllocatingEvaluation`](@ref)) specify whether the gradient works by allocation (default) form `grad_f(M, p)` or [`InplaceEvaluation`](@ref) in place, that is of the form `grad_f!(M, X, p)` and analogously for the Hessian.
  * `retraction_method`:      (`default_retraction_method(M, typeof(p))`) a retraction to use
  * `initial_tangent_vector`: (`zero_vector(M, p)`) initialize any tangent vector data,
  * `maxIterLanczos`:         (`200`) a shortcut to set the stopping criterion in the sub solver,
  * `ρ_regularization`:       (`1e3`) a regularization to avoid dividing by zero for small values of cost and model
  * `stopping_criterion`:     ([`StopAfterIteration`](@ref)`(40) |`[`StopWhenGradientNormLess`](@ref)`(1e-9) |`[`StopWhenAllLanczosVectorsUsed`](@ref)`(maxIterLanczos)`)
  * `sub_state`:              [`LanczosState`](@ref)`(M, copy(M, p); maxIterLanczos=maxIterLanczos, σ=σ) a state for the subproblem or an [`AbstractEvaluationType`](@ref) if the problem is a function.
  * `sub_objective`:          a shortcut to modify the objective of the subproblem used within in the
  * `sub_problem`:            [`DefaultManoptProblem`](@ref)`(M, sub_objective)` the problem (or a function) for the sub problem

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective, respectively. If you provide the [`ManifoldGradientObjective`](@ref) directly, these decorations can still be specified

By default the `debug=` keyword is set to [`DebugIfEntry`](@ref)`(:ρ_denominator, >(0); message="Denominator nonpositive", type=:error)` to avoid that by rounding errors the denominator in the computation of `ρ` gets nonpositive.
