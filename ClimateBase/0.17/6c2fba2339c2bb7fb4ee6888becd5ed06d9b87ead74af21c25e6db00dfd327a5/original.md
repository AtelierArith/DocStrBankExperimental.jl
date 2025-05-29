```
interpolation2pressure(A::ClimArray, P::ClimArray, plevels::Vector; kwargs...) → B
```

Interpolate `A`, which has some arbitrary height dimension (height, model levels, etc.), into a new `B::ClimArray` where the vertical dimension is pressure. `P` is another `ClimArray`, that has the pressure values in Pascal, and otherwise same spatiotemporal structure as `A`. The `plevels` variable denotes which pressure levels `B` should have.

The keword `vertical_dim = Hei()` denotes which dimension of `A` denotes "height". The keyword `extrapolation_bc = Line()` configures extrapolation. It is linear by default, but can be any value such as `extrapolation_bc = NaN`. For other extrapolation methods use the Interpolations.jl package.

Keyword `descending = true` specifies whether pressure is ordered descendingly or ascendingly along the vertical dimension.
