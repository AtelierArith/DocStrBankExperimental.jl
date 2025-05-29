```
WCSSolution{T1,T2,T3} <: TopologicalNumbersSolutions
```

The `WCSSolution` struct represents a solution for finding and calculating the Weyl points.

# Fields

  * `kn::T1`: Compute the Chern number of the plane perpendicular to the `"kn"` direction in Brillouin zone (`"k1"`, `"k2"`, `"k3"`).
  * `param::T2`: Wavenumber parameters in `"kn"` direction.
  * `nums::T3`: The Chern number for each energy bands and each wavenumber parameters.
