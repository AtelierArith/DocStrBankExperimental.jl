```
xy2lonlat(xy::Matrix{<:Real}, s_srs=""; s_srs="", t_srs="+proj=longlat +datum=WGS84")
```

または

```
xy2lonlat(D::GMTdataset, s_srs=""; s_srs="", t_srs="+proj=longlat +datum=WGS84")
```

与えられた投影からXYをLonLatに逆投影します。出力はWGS84であると仮定されます。これが正しくない場合は、`t_srs`オプションを介して適切な投影情報を渡してください（PROJ4、WKT、EPSG）。

### パラメータ

  * `xy`: 入力データ。これは行列、またはGMTdataset（またはそのベクトル）である可能性があります。
  * `s_srs`: データの投影システム。これはPROJ4、WKT文字列、またはEPSGコードである可能性があります。
  * `t_srs`: 目標SRS。デフォルトが満足できない場合は、新しい投影情報（PROJ4、WKT、EPSG）を提供してください。

### 戻り値

入力が行列の場合は行列、入力がそのタイプであった場合はGMTdatasetを返します。
