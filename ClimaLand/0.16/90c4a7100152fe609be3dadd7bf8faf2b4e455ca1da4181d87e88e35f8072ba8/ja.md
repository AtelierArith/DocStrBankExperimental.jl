```
 prescribed_forcing_era5(era5_ncdata_path,
                         surface_space,
                         start_date,
                         earth_param_set,
                         FT;
                         gustiness=1,
                         c_co2 = TimeVaryingInput((t) -> 4.2e-4),
                         time_interpolation_method = LinearInterpolation(PeriodicCalendar()),
                         regridder_type = :InterpolationsRegridder)
```

ERA5データが格納されたnetcdfファイルへのパス、surface*space、開始日、およびearth*param_setから`PrescribedAtmosphere`と`PrescribedRadiativeFluxes`を構築するヘルパー関数です。

引数`era5_ncdata_path`は、すべての変数が必要ですが、異なるファイルで異なる時間間隔を持つncファイルのリストであるか、すべての変数を含む単一のファイルです。
