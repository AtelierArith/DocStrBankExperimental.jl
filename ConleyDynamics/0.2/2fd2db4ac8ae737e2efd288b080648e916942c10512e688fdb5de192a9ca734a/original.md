```
conley_index(lc::LefschetzComplex, subcomp::Vector{String})
```

Determine the Conley index of a Lefschetz complex subset.

The function raises an error if the subset `subcomp` is not locally closed. The computations are performed over the field associated with the Lefschetz complex boundary matrix.
