```
affinityprop(S::AbstractMatrix; [maxiter=200], [tol=1e-6], [damp=0.5],
             [display=:none]) -> AffinityPropResult
```

Perform affinity propagation clustering based on a similarity matrix `S`.

$S_{ij}$ ($i ≠ j$) is the similarity (or the negated distance) between the $i$-th and $j$-th points, $S_{ii}$ defines the *availability* of the $i$-th point as an *exemplar*.

# Arguments

  * `damp::Real`: the dampening coefficient, $0 ≤ \mathrm{damp} < 1$. Larger values indicate slower (and probably more stable) update. $\mathrm{damp} = 0$ disables dampening.
  * `maxiter`, `tol`, `display`: see [common options](@ref common_options)

# References

> Brendan J. Frey and Delbert Dueck. *Clustering by Passing Messages Between Data Points.* Science, vol 315, pages 972-976, 2007.

