```
filter_shallow_pairs(lc::LefschetzComplex, phi)
```

Find all shallow pairs for a filter.

This function finds all shallow pairs for the filter `phi`. These are face-coface pairs `(x,y)` whose dimensions differ by one, and such that `y` has the smallest filter value on the coboundary of `x`, and `x` has the largest filter value on the boundary of `y`.

If the filter is injective, these pairs give rise to a Forman vector field on the underlying Lefschetz complex. For noninjective filters this is not true in general.
