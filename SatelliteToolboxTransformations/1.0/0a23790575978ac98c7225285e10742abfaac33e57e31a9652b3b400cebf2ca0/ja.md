```
jd_utc_to_ut1(JD_UTC::Number, eop::Union{EopIau1980, EopIau2000A}) -> Float64
```

UTCのユリウス日`JD_UTC`を、EOPデータ`eop`によって与えられた累積差を使用してUT1のユリウス日に変換します（[`fetch_iers_eop`](@ref)を参照）。累積差は補間されることに注意してください。
