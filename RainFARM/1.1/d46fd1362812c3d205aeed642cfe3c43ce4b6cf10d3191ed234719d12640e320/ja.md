```
(data, lon, lat, time) = read_netcdf2d(file, varname="")
```

netcdf `file` から変数 `varname` を読み込みます（オプション）。データと座標および時間軸を返します。
