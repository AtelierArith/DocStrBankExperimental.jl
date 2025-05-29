```
shift_longitude(var, lower_lon, upper_lon; shift_by = 0.0)
```

Shift the longitudes in `var` to `lower_lon` to `upper_lon` degrees.

We assume that the units of the longitude dimension is degrees. If this is not the case, then one can use [`convert_dim_units`](@ref) to convert the units to degrees.

This function assumes the prime meridian (0th degree) in `var` is the same before and after shifting the longitudes.

If two points share the same longitude (e.g. -180 degrees and 180 degrees on longitudes spanning from -180 degrees to 180 degrees), then we remove the last longitude before shifting the longitudes. This is necessary to prevent duplicated longitudes after shifting longitudes.

To shift from -180 to 180 degrees to 0 to 360 degrees, use `shift_longitude(var, 0.0, 360.0)` and to shift from 0 to 360 degrees to -180 to 180 degrees, use `shift_longitude(var, -180.0, 180.0)`.
