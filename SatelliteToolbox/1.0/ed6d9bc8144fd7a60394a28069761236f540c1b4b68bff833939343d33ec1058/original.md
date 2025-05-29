```
raan_to_ltdn(raan::Number, t::Union{Number, DateTime}) -> Float64
```

Compute the local time of the ascending node (LTDN) given the `raan` at instant `t` [UT1].

`t` can be represented as a Julian Day [UT1] or `DateTime` [UT1].
