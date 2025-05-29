```
def_time_coord(nc::NCDataset, length=Inf, eltype=Float64;
    units = "seconds since 2020-01-01 00:00:00"
    kwargs...
)
```

Deine a time coordinate (dimension + variable) `"time"` in the NetCDF dataset `nc`. By default its length is set to be unlimited. The variable corresponding to the coordinate is returned.

Additional attributes can be added as keyword arguments.

# Example

```julia
timevar = add_time_coord!(nc; units = "seconds since 2020-01-01 00:00:00",)
timevar[:] = collect(0.0:0.5:60)
```
