```
CSys(sdim::IT1, mdim::IT2) where {IT1<:Integer, IT2<:Integer}
```

Construct coordinate system for isotropic-material used with isoparametric finite elements.

  * `sdim` = number of space dimensions,
  * `mdim` = number of manifold dimensions of the finite element in which the coordinate system  is being evaluated.

!!! note
    If  the coordinate system matrix should be identity, better use the constructor for this specific situation, `CSys(dim)`. That will be much more efficient.


# See also

`gen_iso_csmat`
