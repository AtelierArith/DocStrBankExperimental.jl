```
conjugate_residual(TpM::TangentSpace, A, b, X=zero_vector(TpM))
conjugate_residual(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X=zero_vector(TpM))
conjugate_residual!(TpM::TangentSpace, A, b, X)
conjugate_residual!(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X)
```

Compute the solution of $\mathcal A(p)[X] + b(p) = 0_p$, where

  * $\mathcal A$ is a linear, symmetric operator on $T_{p}\mathcal M$
  * $b$ is a vector field on the manifold
  * $X ∈ T_{p}\mathcal M$ is a tangent vector
  * $0_p$ is the zero vector $T_{p}\mathcal M$.

This implementation follows Algorithm 3 in [LaiYoshise:2024](@cite) and is initalised with $X^{(0)}$ as the zero vector and

  * the initial residual $r^{(0)} = -b(p) - \mathcal A(p)[X^{(0)}]$
  * the initial conjugate direction $d^{(0)} = r^{(0)}$
  * initialize $Y^{(0)} = \mathcal A(p)[X^{(0)}]$

performed the following steps at iteration $k=0,…$ until the `stopping_criterion` is fulfilled.

1. compute a step size $α_k = \displaystyle\frac{⟨ r^{(k)}, \mathcal A(p)[r^{(k)}] ⟩_p}{⟨ \mathcal A(p)[d^{(k)}], \mathcal A(p)[d^{(k)}] ⟩_p}$
2. do a step $X^{(k+1)} = X^{(k)} + α_kd^{(k)}$
3. update the residual $r^{(k+1)} = r^{(k)} + α_k Y^{(k)}$
4. compute $Z = \mathcal A(p)[r^{(k+1)}]$
5. Update the conjugate coefficient $β_k = \displaystyle\frac{⟨ r^{(k+1)}, \mathcal A(p)[r^{(k+1)}] ⟩_p}{⟨ r^{(k)}, \mathcal A(p)[r^{(k)}] ⟩_p}$
6. Update the conjugate direction $d^{(k+1)} = r^{(k+1)} + β_kd^{(k)}$
7. Update  $Y^{(k+1)} = -Z + β_k Y^{(k)}$

Note that the right hand side of Step 7 is the same as evaluating $\mathcal A[d^{(k+1)}]$, but avoids the actual evaluation

# Input

  * `TpM` the [`TangentSpace`](@extref `ManifoldsBase.TangentSpace`) as the domain
  * `A` a symmetric linear operator on the tangent space `(M, p, X) -> Y`
  * `b` a vector field on the tangent space `(M, p) -> X`
  * `X` the initial tangent vector

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(M)`[`|`](@ref StopWhenAny)[`StopWhenRelativeResidualLess`](@ref)`(c,1e-8)`,  where `c` is $\lVert b \rVert_{}$: a functor indicating that the stopping criterion is fulfilled

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
