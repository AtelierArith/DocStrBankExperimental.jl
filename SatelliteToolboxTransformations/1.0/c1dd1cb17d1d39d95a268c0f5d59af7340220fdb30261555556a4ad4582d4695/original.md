```
jd_tt_to_utc(JD_TT::Number, ΔAT::Number) -> Float64
```

Convert the Julian Day in TT `JD_TT` (Terrestrial Time) to the Julian Day in UTC (Terrestrial Time) using the accumulated difference `ΔAT` between UTC and the International Atomic Time (TAI). If no value is provided, then the leap seconds will be obtained from the table `ΔAT_Data`. **Notice that, in this case, if a date previous to 1973 is provided, then a fixed value of 10 will be used, leading to wrong computations.**
