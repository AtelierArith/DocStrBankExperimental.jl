```
quasi_Newton(M, f, grad_f, p; kwargs...)
quasi_Newton!(M, f, grad_f, p; kwargs...)
```

Perform a quasi Newton iteration to solve

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} f(p)
$$

with start point `p`. The iterations can be done in-place of `p`$=p^{(0)}$. The $k$th iteration consists of

1. Compute the search direction $η^{(k)} = -\mathcal B_k [\operatorname{grad}f (p^{(k)})]$ or solve $\mathcal H_k [η^{(k)}] = -\operatorname{grad}f (p^{(k)})]$.
2. Determine a suitable stepsize $α_k$ along the curve $γ(α) = R_{p^{(k)}}(α η^{(k)})$, usually by using [`WolfePowellLinesearch`](@ref).
3. Compute $p^{(k+1)} = R_{p^{(k)}}(α_k η^{(k)})$.
4. Define $s_k = \mathcal T_{p^{(k)}, α_k η^{(k)}}(α_k η^{(k)})$ and $y_k = \operatorname{grad}f(p^{(k+1)}) - \mathcal T_{p^{(k)}, α_k η^{(k)}}(\operatorname{grad}f(p^{(k)}))$, where $\mathcal T$ denotes a vector transport.
5. Compute the new approximate Hessian $H_{k+1}$ or its inverse $B_{k+1}$.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `basis=`[`DefaultOrthonormalBasis`](@extref ManifoldsBase.DefaultOrthonormalBasis)`()`: basis to use within each of the the tangent spaces to represent the Hessian (inverse) for the cases where it is stored in full (matrix) form.
  * `cautious_update=false`:  whether or not to use the [`QuasiNewtonCautiousDirectionUpdate`](@ref)  which wraps the `direction_upate`.
  * `cautious_function=(x) -> x * 1e-4`: a monotone increasing function for the cautious update that is zero at $x=0$ and strictly increasing at $0$
  * `direction_update=`[`InverseBFGS`](@ref)`()`: the [`AbstractQuasiNewtonUpdateRule`](@ref) to use.
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.For example `grad_f(M,p)` allocates, but `grad_f!(M, X, p)` computes the result in-place of `X`.
  * `initial_operator= initial_scale*Matrix{Float64}(I, n, n)`:  initial matrix to use in case the Hessian (inverse) approximation is stored as a full matrix,  that is `n=manifold_dimension(M)`. This matrix is only allocated for the full matrix case.  See also `initial_scale`.
  * `initial_scale=1.0`: scale initial `s` to use in with $\frac{s⟨s_k,y_k⟩_{p_k}}{\lVert y_k\rVert_{p_k}}$ in the computation of the limited memory approach. see also `initial_operator`
  * `memory_size=20`: limited memory, number of $s_k, y_k$ to store.  Set to a negative value to use a full memory (matrix) representation
  * `nondescent_direction_behavior=:reinitialize_direction_update`: specify how non-descent direction is handled. This can be

      * `:step_towards_negative_gradient`: the direction is replaced with negative gradient, a message is stored.
      * `:ignore`: the verification is not performed, so any computed direction is accepted. No message is stored.
      * `:reinitialize_direction_update`: discards operator state stored in direction update rules.
      * any other value performs the verification, keeps the direction but stores a message.

    A stored message can be displayed using [`DebugMessages`](@ref).
  * `preconditioner=nothing` specify a preconditioner, either

      * the default `nothing` does not activate a preconditioning
      * a function of the form `(M, p, X) -> Y` or mutating `(M, Y, p, X) -> Y` depending on the `evaluation`
      * a [`PreconditionedDirection`](@ref). See also their docs for mor details on the preconditioner.

    Note that the preconditioner is applied to the gradient, i.e. the right hand side *before* solving the linear system.
  * `project!=copyto!`: for numerical stability it is possible to project onto the tangent space after every iteration. the function has to work inplace of `Y`, that is `(M, Y, p, X) -> Y`, where `X` and `Y` can be the same memory.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`WolfePowellLinesearch`](@ref)`(retraction_method, vector_transport_method)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(max(1000, memory_size))`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
