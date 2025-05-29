```
build_measure(expr::JuMP.AbstractJuMPScalar,
              data::AbstractMeasureData)::Measure
```

Build and return a [`Measure`](@ref) given the expression to be measured `expr` using measure data `data`. This principally serves as an internal method for measure definition. Errors if the supports associated with `data` violate an finite variable parameter bounds of finite variables that are included in the measure.
