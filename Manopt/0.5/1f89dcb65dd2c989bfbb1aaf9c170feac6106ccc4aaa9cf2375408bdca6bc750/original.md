```
DouglasRachford(M, f, proxes_f, p)
DouglasRachford(M, mpo, p)
DouglasRachford!(M, f, proxes_f, p)
DouglasRachford!(M, mpo, p)
```

Compute the Douglas-Rachford algorithm on the manifold $\mathcal M$, starting from `p``given the (two) proximal maps`proxes_f`, see [ BergmannPerschSteidl:2016](@cite).

For $k>2$ proximal maps, the problem is reformulated using the parallel Douglas Rachford: a vectorial proximal map on the power manifold $\mathcal M^k$ is introduced as the first proximal map and the second proximal map of the is set to the [`mean`](@extref Statistics.mean-Tuple{AbstractManifold, Vararg{Any}}) (Riemannian center of mass). This hence also boils down to two proximal maps, though each evaluates proximal maps in parallel, that is, component wise in a vector.

!!! note



The parallel Douglas Rachford does not work in-place for now, since    while creating the new staring point `p'` on the power manifold, a copy of `p`    Is created

If you provide a [`ManifoldProximalMapObjective`](@ref) `mpo` instead, the proximal maps are kept unchanged.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `proxes_f`: functions of the form `(M, λ, p)-> q` performing a proximal maps, where `⁠λ` denotes the proximal parameter, for each of the summands of `F`. These can also be given in the [`InplaceEvaluation`](@ref) variants `(M, q, λ p) -> q` computing in place of `q`.
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `α= k -> 0.9`: relaxation of the step from old to new iterate, to be precise $p^{(k+1)} = g(α_k; p^{(k)}, q^{(k)})$, where $q^{(k)}$ is the result of the double reflection involved in the DR algorithm and $g$ is a curve induced by the retraction and its inverse.
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`) This is used both in the relaxation step as well as in the reflection, unless you set `R` yourself.
  * `λ= k -> 1.0`: function to provide the value for the proximal parameter $λ_k$
  * `R=reflect(!)`:           method employed in the iteration to perform the reflection of `p` at the prox of `p`. This uses by default [`reflect`](@ref) or `reflect!` depending on `reflection_evaluation` and the retraction and inverse retraction specified by `retraction_method` and `inverse_retraction_method`, respectively.
  * `reflection_evaluation`: ([`AllocatingEvaluation`](@ref) whether `R` works in-place or allocating
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`) This is used both in the relaxation step as well as in the reflection, unless you set `R` yourself.
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-5)`: a functor indicating that the stopping criterion is fulfilled
  * `parallel=false`: indicate whether to use a parallel Douglas-Rachford or not.

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
