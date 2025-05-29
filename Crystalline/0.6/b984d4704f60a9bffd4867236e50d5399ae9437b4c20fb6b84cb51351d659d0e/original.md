```
lgirreps(sgnum::Integer, D::Union{Val{Int}, Integer}=Val(3))
                                        -> Dict{String, Collection{LGIrrep{D}}}
```

For given space group number `sgnum` and dimension `D`, return the associated little group (or "small") irreps (`LGIrrep{D}`s) at high-symmetry k-points, lines, and planes. 

Returns a `Dict` with little group **k**-point labels as keys and vectors of `LGIrrep{D}`s as values.

## Notes

  * The returned irreps are complex in general. Real irreps (as needed in time-reversal invariant settings) can subsequently be obtained with the [`realify`](@ref) method.
  * Returned irreps are spinless.
  * The irrep labelling follows CDML conventions.
  * Irreps along lines or planes may depend on free parameters `αβγ` that parametrize the **k** point. To evaluate the irreps at a particular value of `αβγ` and return the associated matrices, use `(lgir::LGIrrep)(αβγ)`. If `αβγ` is an empty tuple in this call, the matrices associated with `lgir` will be evaluated assuming `αβγ = [0,0,...]`.

## References

The underlying data is sourced from the ISOTROPY ISO-IR dataset. Please cite the original reference material associated with ISO-IR:

1. Stokes, Hatch, & Campbell,  [ISO-IR, ISOTROPY Software Suite](https://stokes.byu.edu/iso/irtables.php).
2. Stokes, Campbell, & Cordes, [Acta Cryst. A. **69**, 388-395 (2013)](https://doi.org/10.1107/S0108767313007538).

The ISO-IR dataset is occasionally missing some **k**-points that lie outside the basic domain but still resides in the representation domain (i.e. **k**-points with postscripted 'A', 'B', etc. labels, such as 'ZA'). In such cases, the missing irreps may instead have been manually sourced from the Bilbao Crystallographic Database.
