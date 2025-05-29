```
 homogeneity_test(px, cov_corr; ks, criteria)
```

Iterate over `Parcel`s within a `Parcellation`, testing the homogeneity of each.

Optionally supply a set of parcel keys `ks`, which are not necessarily those of `px`! (The idea is to allow the possibility of using a fixed set of keys across many calls to this function, and the `Parcellation`s passed each time may not exactly share all of them. See the method below that accepts a `Vector{Parcellation{T}}`.)
