```julia
ScaleBonds!(uc::UnitCell, dist::Float64, scale::Number)
ScaleBonds!(uc::UnitCell, label::String, scale::Number)
```

Scale the matrix of an existing bond in the `UnitCell` with the given `label`, or at a given distance=`dist`, by the given scaling factor.
