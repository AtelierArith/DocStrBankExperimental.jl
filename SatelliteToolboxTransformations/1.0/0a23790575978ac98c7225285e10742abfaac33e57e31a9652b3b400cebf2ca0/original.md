```
jd_utc_to_ut1(JD_UTC::Number, eop::Union{EopIau1980, EopIau2000A}) -> Float64
```

Convert the Julian Day in UTC `JD_UTC` to the Julian Day in UT1 using the accumulated difference given by the EOP Data `eop` (see [`fetch_iers_eop`](@ref)).  Notice that the accumulated difference will be interpolated.
