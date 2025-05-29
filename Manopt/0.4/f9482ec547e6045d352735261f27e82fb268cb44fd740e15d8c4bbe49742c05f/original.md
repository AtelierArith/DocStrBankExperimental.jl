```
quasi_Newton(M, f, grad_f, p)
```

Perform a quasi Newton iteration for `f` on the manifold `M` starting in the point `p`.

The $k$th iteration consists of

1. Compute the search direction $η_k = -\mathcal{B}_k [\operatorname{grad}f (p_k)]$ or solve $\mathcal{H}_k [η_k] = -\operatorname{grad}f (p_k)]$.
2. Determine a suitable stepsize $α_k$ along the curve $\gamma(α) = R_{p_k}(α η_k)$, usually by using [`WolfePowellLinesearch`](@ref).
3. Compute `p_{k+1} = R_{p_k}(α_k η_k)``.
4. Define $s_k = T_{p_k, α_k η_k}(α_k η_k)$ and $y_k = \operatorname{grad}f(p_{k+1}) - T_{p_k, α_k η_k}(\operatorname{grad}f(p_k))$.
5. Compute the new approximate Hessian $H_{k+1}$ or its inverse $B_k$.

# Input

  * `M`      a manifold $\mathcal{M}$.
  * `f`      a cost function $F : \mathcal{M} →ℝ$ to minimize.
  * `grad_f` the gradient $\operatorname{grad}F : \mathcal{M} →T_x\mathcal M$ of $F$.
  * `p`      an initial value $p ∈ \mathcal{M}$.

# Optional

  * `basis`:                   (`DefaultOrthonormalBasis()`) basis within the tangent spaces

to represent the Hessian (inverse).

  * `cautious_update`:         (`false`) whether or not to use a [`QuasiNewtonCautiousDirectionUpdate`](@ref)
  * `cautious_function`:       (`(x) -> x*10^(-4)`) a monotone increasing function that is zero at 0 and strictly increasing at 0 for the cautious update.
  * `direction_update`:        ([`InverseBFGS`](@ref)`()`) the update rule to use.
  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) specify whether the gradient works by  allocation (default) form `gradF(M, p)` or [`InplaceEvaluation`](@ref) in place of form `gradF!(M, X, p)`.
  * `initial_operator`:        (`Matrix{Float64}(I, n, n)`) initial matrix to use die the approximation, where `n=manifold_dimension(M)`, see also `scale_initial_operator`.
  * `memory_size`:             (`20`) limited memory, number of $s_k, y_k$ to store. Set to a negative value to use a full memory representation
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) a retraction method to use
  * `scale_initial_operator`:  (`true`) scale initial operator with $\frac{⟨s_k,y_k⟩_{p_k}}{\lVert y_k\rVert_{p_k}}$ in the computation
  * `stabilize`:               (`true`) stabilize the method numerically by projecting computed (Newton-) directions to the tangent space to reduce numerical errors
  * `stepsize`:                ([`WolfePowellLinesearch`](@ref)`(retraction_method, vector_transport_method)`) specify a [`Stepsize`](@ref).
  * `stopping_criterion`:      ([`StopAfterIteration`](@ref)`(max(1000, memory_size)) |`[`StopWhenGradientNormLess`](@ref)`(1e-6)`) specify a [`StoppingCriterion`](@ref)
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) a vector transport to use.
  * `nondescent_direction_behavior`: (`:reinitialize_direction_update`) specify how non-descent direction is handled. This can be

      * `:step_towards_negative_gradient`: the direction is replaced with negative gradient, a message is stored.
      * `:ignore`: the verification is not performed, so any computed direction is accepted. No message is stored.
      * `:reinitialize_direction_update`: discards operator state stored in direction update rules.
      * any other value performs the verification, keeps the direction but stores a message.

    A stored message can be displayed using [`DebugMessages`](@ref).

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details.
