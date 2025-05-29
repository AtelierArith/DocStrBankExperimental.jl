```
center_longitude!(var::OutputVar, lon::Real)
```

Shift the longitudes in `var` so that `lon` is the center one.

This is useful to center the global projection to the 180 meridian instead of the 0.

!!! warn "Deprecated"
    This function is deprecated and users are encouraged to use [`shift_longitude`](@ref) instead.

