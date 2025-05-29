```
AnalysisSurfaceIntegral{Variable, NBoundaries}(boundary_symbols::NTuple{NBoundaries, Symbol},
                                               variable)
```

This struct is used to compute the surface integral of a quantity of interest `variable` alongside the boundary/boundaries associated with particular names given in `boundary_symbols`. For instance, this can be used to compute the lift [`LiftCoefficientPressure2D`](@ref) or drag coefficient [`DragCoefficientPressure2D`](@ref) of e.g. an 2D airfoil with the boundary names `:AirfoilTop`, `:AirfoilBottom` which would be supplied as  `boundary_symbols = (:AirfoilTop, :AirfoilBottom)`. A single boundary name can also be supplied, e.g. `boundary_symbols = (:AirfoilTop,)`.

  * `boundary_symbols::NTuple{NBoundaries, Symbol}`: Name(s) of the boundary/boundaries where the quantity of interest is computed
  * `variable::Variable`: Quantity of interest, like lift or drag
