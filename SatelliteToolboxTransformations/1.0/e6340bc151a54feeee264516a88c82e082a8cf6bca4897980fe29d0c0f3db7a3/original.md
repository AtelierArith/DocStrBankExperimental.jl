```
jd_utc_to_tt(JD_UTC::Number[, ΔAT::Number]) -> Float64
```

Convert the Julian Day in UTC `JD_UTC` to the Julian Day in TT (Terrestrial Time) using the accumulated difference `ΔAT` between UTC and the International Atomic Time (TAI). If no value is provided, then the leap seconds will be obtained from the table `ΔAT_Data`. **Notice that, in this case, if a date previous to 1973 is provided, then a fixed value of 10 will be used, leading to wrong computations.**
