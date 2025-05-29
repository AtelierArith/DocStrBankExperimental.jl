```
get_forcing(simulation::DiscretizedSPAC)
```

Returns a DataFrame with amounts (and isotopoic compositions) of the input forcing. Note that meteorologic forcing (amounts and isotopic signatures) is same as in input csvs, vegetation evolution (lai, height, sai) have been transformed to absolute units.

```
 Row │ dates                globrad_MJDayM2  tmax_degC  tmin_degC  vappres_kPa  windspeed_ms  prec_mmDay  precdelta18O_permil  precdelta2H_permil  densef_percent  height_m  lai_m2m2  sai_m2m2
     │ DateTime             Float64          Float64    Float64    Float64      Float64       Float64     Float64              Float64             Float64         Float64   Float64   Float64
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 2021-01-01T00:00:00             5.53        0.9      -10.1         0.26           1.5         0.0               -15.04             -111.96           100.0      25.0       2.1       1.0
   2 │ 2021-01-02T00:00:00             5.1        -0.6       -9.3         0.3            1.6         0.0               -15.04             -111.96           100.0      25.0       2.1       1.0
```
