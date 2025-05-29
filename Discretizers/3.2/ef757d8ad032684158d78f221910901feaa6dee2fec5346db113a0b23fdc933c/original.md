```
LinearDiscretizer
```

A discretizer which encodes (typically) continuous values into discrete bins. A univariate domain is divided into discrete by edges. A value V will be encoded into bin B if V ∈ [Bₗ Bᵣ) (or V ∈ [Bₗ Bᵣ] if B is the rightmost bin)

If force*outliers*to_closest is set to true, then values outside of binedges will be shunted into the nearest bin. Otherwise an error is thrown.

TODO(tim):     handle NA     handle Nullable     handle NaN     ability to specify decoding behavior
