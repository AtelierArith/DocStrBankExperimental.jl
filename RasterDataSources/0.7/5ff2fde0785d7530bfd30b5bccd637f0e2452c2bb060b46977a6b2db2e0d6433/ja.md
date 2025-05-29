```
getraster(source::Type{CHELSA{BioClim}}, [layer]; version = 2, [patch]) => Union{Tuple,String}
```

[`CHELSA`](@ref) [`BioClim`](@ref) データを [chelsa-climate.org](https://chelsa-climate.org/) からダウンロードします。

# 引数

  * `layer`: `[:bio1, :bio2, :bio3, :bio4, :bio5, :bio6, :bio7, :bio8, :bio9, :bio10, :bio11, :bio12, :bio13, :bio14, :bio15, :bio16, :bio17, :bio18, :bio19, :hurs_max, :clt_max, :sfcWind_max, :vpd_max, :rsds_max, :pet_penman_max, :cmi_max, :hurs_min, :clt_min, :sfcWind_min, :vpd_min, :rsds_min, :pet_penman_min, :cmi_min, :hurs_mean, :clt_mean, :sfcWind_mean, :vpd_mean, :rsds_mean, :pet_penman_mean, :cmi_mean, :hurs_range, :clt_range, :sfcWind_range, :vpd_range, :rsds_range, :pet_penman_range, :cmi_range, :gdd0, :gddlgd0, :gdgfgd0, :ngd0, :gdd5, :gddlgd5, :gdgfgd5, :ngd5, :gdd10, :gddlgd10, :gdgfgd10, :ngd10, :fcf, :fgd, :lgd, :scd, :gsl, :gst, :gsp, :npp, :swb, :swe, :kg0, :kg1, :kg2, :kg3, :kg4, :kg5]` の `Symbol` の iterable。`layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード引数

  * `version`: 現在の CHELSA バージョンを示す `Integer`、現在は `1` または `2` のいずれか。
  * `patch`: CHELSA パッチ番号を示す `Integer`。最新のパッチ (V1.2 および V2.1) がデフォルトです。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
