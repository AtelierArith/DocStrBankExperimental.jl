```
get_forcing(simulation::DiscretizedSPAC)
```

入力強制の量（および同位体組成）を含むDataFrameを返します。気象強制（量と同位体署名）は入力csvと同じであり、植生の進化（lai、高さ、sai）は絶対単位に変換されています。

```
 Row │ dates                globrad_MJDayM2  tmax_degC  tmin_degC  vappres_kPa  windspeed_ms  prec_mmDay  precdelta18O_permil  precdelta2H_permil  densef_percent  height_m  lai_m2m2  sai_m2m2
     │ DateTime             Float64          Float64    Float64    Float64      Float64       Float64     Float64              Float64             Float64         Float64   Float64   Float64
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 2021-01-01T00:00:00             5.53        0.9      -10.1         0.26           1.5         0.0               -15.04             -111.96           100.0      25.0       2.1       1.0
   2 │ 2021-01-02T00:00:00             5.1        -0.6       -9.3         0.3            1.6         0.0               -15.04             -111.96           100.0      25.0       2.1       1.0
```
