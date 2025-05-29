```
StabilityCircle(S11, S12, S21, S22, inout::Symbol, Np; stable = false)
```

Computes the region of stability (or unstability) and returns a Makie.Polygon.

  * Sii: S-parameter
  * inout: a symbol selecting source or load regions. Valid values are :load or :source.
  * Np: Number of points.
  * stable: Selects if the region corresponds to the stable (true) or unstable (false) region.
