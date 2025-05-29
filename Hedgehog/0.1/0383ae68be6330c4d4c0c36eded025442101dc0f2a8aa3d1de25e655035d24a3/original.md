```
add_yearfrac(t::Real, yf::Real) -> Real
```

Add a fractional number of years (`yf`, computed as ACT/365) to a timestamp `t`.

The timestamp `t` is assumed to be in milliseconds since the Julia `Dates` module epoch (0000-01-01T00:00:00). Returns the updated timestamp in milliseconds as `Float64`.

This version is AD-compatible.
