```
 DouglasRachford!(M, f, proxes_f, p)
 DouglasRachford!(M, mpo, p)
```

Compute the Douglas-Rachford algorithm on the manifold $\mathcal M$, initial data $p ∈ \mathcal M$ and the (two) proximal maps `proxes_f` in place of `p`.

For $k>2$ proximal maps, the problem is reformulated using the parallel Douglas Rachford: a vectorial proximal map on the power manifold $\mathcal M^k$ is introduced as the first proximal map and the second proximal map of the is set to the `mean` (Riemannian Center of mass). This hence also boils down to two proximal maps, though each evaluates proximal maps in parallel, that is component wise in a vector.

!!! note
    While creating the new staring point `p'` on the power manifold, a copy of `p` Is created, so that the (by k>2 implicitly generated) parallel Douglas Rachford does not work in-place for now.


If you provide a [`ManifoldProximalMapObjective`](@ref) `mpo` instead, the proximal maps are kept unchanged.

# Input

  * `M`:        a Riemannian Manifold $\mathcal M$
  * `f`:        a cost function consisting of a sum of cost functions
  * `proxes_f`: functions of the form `(M, λ, p)->q` or `(M, q, λ, p)->q` performing a proximal map, where `⁠λ` denotes the proximal parameter, for each of the summands of `f`.
  * `p`:        initial point $p ∈ \mathcal M$

For more options, see [`DouglasRachford`](@ref).
