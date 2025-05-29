```
jd_utc_to_ut1(JD_UTC::Number, eop::Union{EopIau1980, EopIau2000A}) -> Float64
```

UT1のジュリアンデイ`JD_UT1`を、EOPデータ`eop`によって与えられた累積差を使用してUTCのジュリアンデイに変換します（[`fetch_iers_eop`](@ref）を参照）。累積差は補間されることに注意してください。
