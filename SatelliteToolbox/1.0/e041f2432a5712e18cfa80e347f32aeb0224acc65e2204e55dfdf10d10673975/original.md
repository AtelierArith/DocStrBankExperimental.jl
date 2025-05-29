```
ltan_to_raan(ltan::Union{Number, Time}, t::Union{Number, DateTime}) -> Float64
```

Compute the RAAN [0, 2π] [rad] so that the local time of ascending node (LTAN) is `ltan` at instant `t` [UT1].

`ltan` can be represented as a `Number`, indicating the hour, or by a `Time` object.

`t` can be represented as a Julian Day [UT1] or `DateTime` [UT1].
