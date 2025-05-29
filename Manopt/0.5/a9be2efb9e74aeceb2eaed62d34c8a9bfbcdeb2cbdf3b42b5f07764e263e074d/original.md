```
ApproxHessianSymmetricRankOne{E, P, G, T, B<:AbstractBasis{ℝ}, VTR, R<:Real} <: AbstractApproxHessian
```

A functor to approximate the Hessian by the symmetric rank one update.

# Fields

  * `gradient!!`: the gradient function (either allocating or mutating, see `evaluation` parameter).
  * `ν`: a small real number to ensure that the denominator in the update does not become too small and thus the method does not break down.
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`).

## Internal temporary fields

  * `p_tmp`: a temporary storage the current point `p`.
  * `grad_tmp`: a temporary storage for the gradient at the current `p`.
  * `matrix`: a temporary storage for the matrix representation of the approximating operator.
  * `basis`: a temporary storage for an orthonormal basis at the current `p`.

# Constructor

```
ApproxHessianSymmetricRankOne(M, p, gradF; kwargs...)
```

## Keyword arguments

  * `initial_operator` (`Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M))`) the matrix representation of the initial approximating operator.
  * `basis` (`DefaultOrthonormalBasis()`) an orthonormal basis in the tangent space of the initial iterate p.
  * `nu` (`-1`)
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
