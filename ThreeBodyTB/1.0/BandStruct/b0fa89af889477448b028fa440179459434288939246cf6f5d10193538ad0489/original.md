```
function band_summary(tbc, kgrid, fermi=missing)
```

Produces summary of band structure. See below functions for more specific versions of function that automatically generate the k-points.

Note: gaps are not well-defined for non-magnetic systems with odd numbers of electrons, as they are required to be metals.

Returns `direct_gap, indirect_gap, gaptype, bandwidth`

-`direct_gap`: minimum gap at one k-point between nominally filled and empty bands. Can be non-zero in metals.   -`indirect_gap`: LUMO - HOMO. Can be negative if material has a direct gap everywhere, but the conduction band at some k-point is below the valence band at a different k-point. Physically these are indirect gap semimetals.   -`gaptype` : is `:metal` for all metals, `:direct` or `:indirect` for insulators. -`bandwidth` : HOMO - minimum*band*energy. Included semicore states if they are in the TB calculation.
