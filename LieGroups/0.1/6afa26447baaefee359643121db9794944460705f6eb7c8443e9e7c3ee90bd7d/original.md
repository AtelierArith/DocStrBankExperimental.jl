```
log(G, g)
log!(G, X, g)
```

Compute the Lie group logarithm function on the [`OrthogonalGroup`](@ref) $\mathrm{O}(4)$ or [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(4)$, where `e` is the [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` and `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) for dispatch.

The implementation is based on a generalized variant of the Rodrigues' like formula. For details, see [GallierXu:2002; Section 3](@cite).

This result can be computed in-place of `X`

Note the logarithmic map is only locally around the identity uniquely determined.
