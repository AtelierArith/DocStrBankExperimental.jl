```
 prescribed_lai_era5(era5_lai_ncdata_path,
                     era5_lai_cover_ncdata_path,
                     surface_space,
                     start_date,
                     earth_param_set;
                     time_interpolation_method = LinearInterpolation(PeriodicCalendar()),
                     regridder_type = :InterpolationsRegridder)
```

Leaf Area IndexのためのTimeVaryingInputオブジェクトを構築するヘルパー関数で、ERA5 LAIデータが格納されたnetcdfファイルへのファイルパス、ERA5 LAIカバーデータが格納されたnetcdfファイルへのファイルパス、surface*space、開始日、およびearth*param_setを受け取ります。

現在のところ、era5 laiとera5 laiカバーデータの両方に対して単一のファイルが渡された場合にのみ機能します。
