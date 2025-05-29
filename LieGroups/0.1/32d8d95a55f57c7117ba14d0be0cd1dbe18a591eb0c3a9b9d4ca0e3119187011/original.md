```
exp(G, e, X)
exp!(G, e, g, X)
```

Compute the Lie group exponential function on the [`OrthogonalGroup`](@ref) $\mathrm{O}(4)$ or [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(4)$, where `e` is the [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` and `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) for dispatch.

Similar to the $3×3$ case, an efficient computation is provided, adapted from [GallierXu:2002](@cite), [AndricaRohan:2013](@cite) with a few numerical stabilisations.
