```
ApproxHessianBFGS{E, P, G, T, B<:AbstractBasis{ℝ}, VTR, R<:Real} <: AbstractApproxHessian
```

A functor to approximate the Hessian by the BFGS update.

# Fields

  * `gradient!!` the gradient function (either allocating or mutating, see `evaluation` parameter).
  * `scale`
  * `vector_transport_method` a vector transport to use.

## Internal temporary fields

  * `p_tmp` a temporary storage the current point `p`.
  * `grad_tmp` a temporary storage for the gradient at the current `p`.
  * `matrix` a temporary storage for the matrix representation of the approximating operator.
  * `basis` a temporary storage for an orthonormal basis at the current `p`.

# Constructor

```
ApproxHessianBFGS(M, p, gradF; kwargs...)
```

## Keyword arguments

  * `initial_operator` (`Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M))`) the matrix representation of the initial approximating operator.
  * `basis` (`DefaultOrthonormalBasis()`) an orthonormal basis in the tangent space of the initial iterate p.
  * `nu` (`-1`)
  * `evaluation` ([`AllocatingEvaluation`](@ref)) whether the gradient is given as an allocation function or an in-place ([`InplaceEvaluation`](@ref)).
  * `vector_transport_method` (`ParallelTransport()`) vector transport $\mathcal T_{\cdot\gets\cdot}$ to use.
