```
add_yearfrac(t::TimeType, yf::Real) -> DateTime
```

Add a fractional number of years (`yf`, computed as ACT/365) to a `Date` or `DateTime` `t`.

Converts `t` to milliseconds since the Julia `Dates` module epoch, adds the duration corresponding to `yf`, and converts the result back to a `DateTime` object.
