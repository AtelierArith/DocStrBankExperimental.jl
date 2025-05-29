```
ltdn_to_raan(ltdn::Union{Number, Time}, t::Union{Number, DateTime}) -> Float64
```

Compute the RAAN [0, 2π] [rad] so that the local time of descending node (LTAN) is `ltdn` at instant `t` [UT1].

`ltdn` can be represented as a `Number`, indicating the hour, or by a `Time` object.

`t` can be represented as a Julian Day [UT1] or `DateTime` [UT1].
