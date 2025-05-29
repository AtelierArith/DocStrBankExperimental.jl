```
slice(var::OutputVar, kwargs...)
```

Return a new OutputVar by slicing across dimensions as defined by the keyword arguments.

When a time dimension is selected and `start_date` is among `var`'s attributes, it is possible to directly pass a `Dates.DateTime` and `slice` will automatically convert it into the corresponding time.

# Example

```julia
slice(var, lat = 30, lon = 20, time = 100)
```

If `var` has `start_date` among its attributes.

```julia
import Dates
slice(var, lat = 30, lon = 20, time = Dates.DateTime(2020, 12, 21))
```

!!! compat "Support for Dates and generalized dimension names"
    Calling `slice` with a `DateTime` and specifying a dimension by one of its name (instead of the actual name in the file) was introduced in ClimaAnalysis v0.5.17.

