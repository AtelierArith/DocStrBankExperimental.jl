```
add_measure(model::InfiniteModel, meas::Measure,
            name::String = "measure")::GeneralVariableRef
```

Add a measure to `model` and return the corresponding measure reference. This operates in a manner similar to `JuMP.add_variable`. Note this intended as an internal method.
