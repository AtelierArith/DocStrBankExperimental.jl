```
DouglasRachford(M, f, proxes_f, p)
DouglasRachford(M, mpo, p)
```

Compute the Douglas-Rachford algorithm on the manifold $\mathcal M$, initial data $p$ and the (two) proximal maps `proxMaps`, see [ BergmannPerschSteidl:2016](@cite).

For $k>2$ proximal maps, the problem is reformulated using the parallel Douglas Rachford: a vectorial proximal map on the power manifold $\mathcal M^k$ is introduced as the first proximal map and the second proximal map of the is set to the `mean` (Riemannian Center of mass). This hence also boils down to two proximal maps, though each evaluates proximal maps in parallel, that is, component wise in a vector.

If you provide a [`ManifoldProximalMapObjective`](@ref) `mpo` instead, the proximal maps are kept unchanged.

# Input

  * `M`:        a Riemannian Manifold $\mathcal M$
  * `F`:        a cost function consisting of a sum of cost functions
  * `proxes_f`: functions of the form `(M, λ, p)-> q` performing a proximal maps, where `⁠λ` denotes the proximal parameter, for each of the summands of `F`. These can also be given in the [`InplaceEvaluation`](@ref) variants `(M, q, λ p) -> q` computing in place of `q`.
  * `p`:        initial data $p ∈ \mathcal M$

# Optional values

  * `evaluation`:            ([`AllocatingEvaluation`](@ref)) specify whether the proximal maps work by allocation (default) form `prox(M, λ, x)` or [`InplaceEvaluation`](@ref) in-place
  * `λ`:                     (`(iter) -> 1.0`) function to provide the value for the proximal parameter during the calls
  * `α`:                     (`(iter) -> 0.9`) relaxation of the step from old to new iterate, to be precise $t_{k+1} = g(α_k; t_k, s_k)$, where $s_k$ is the result of the double reflection involved in the DR algorithm
  * `inverse_retraction_method` - (`default_inverse_retraction_method(M, typeof(p))`) the inverse retraction to use within

      * the reflection (ignored, if you set `R` directly)
      * the relaxation step
  * `R`:                     method employed in the iteration to perform the reflection of `x` at the prox `p`. This uses by default [`reflect`](@ref) or `reflect!` depending on `reflection_evaluation` and the retraction and inverse retraction specified by `retraction_method` and `inverse_retraction_method`, respectively.
  * `reflection_evaluation`: ([`AllocatingEvaluation`](@ref) whether `R` works in-place or allocating
  * `retraction_method`:     (`default_retraction_metiod(M, typeof(p))`) the retraction to use in

      * the reflection (ignored, if you set `R` directly)
      * the relaxation step
  * `stopping_criterion`:    ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenChangeLess`](@ref)`(1e-5)`) a [`StoppingCriterion`](@ref).
  * `parallel`:              (`false`) indicate whether to use a parallel Douglas-Rachford or not.

and the ones that are passed to [`decorate_state!`](@ref) for decorators.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
