```
lonlat2xy(lonlat::Matrix{<:Real}; t_srs, s_srs="+proj=longlat +datum=WGS84")
```

または

```
lonlat2xy(D::GMTdataset; t_srs, s_srs="+proj=longlat +datum=WGS84")
```

指定された投影法において、LatLonからXYへの前方投影を計算します。入力はWGS84であると仮定されます。そうでない場合は、`s_srs`オプションを介して適切な投影情報を渡してください（PROJ4、WKT、EPSG）。

### パラメータ

  * `lonlat`: 入力データ。これは行列、またはGMTdataset（またはそのベクトル）である可能性があります。
  * `t_srs`: 目的の投影システム。これはPROJ4、WKT文字列、またはEPSGコードである可能性があります。

### 戻り値

入力が行列の場合は行列を、入力がそのタイプであった場合はGMTdatasetを返します。
