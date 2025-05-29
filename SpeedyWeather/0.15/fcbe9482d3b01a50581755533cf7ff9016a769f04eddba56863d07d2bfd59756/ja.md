定常海洋気候学で、月ごとの海面温度フィールドをファイルから読み込み、予測変数に保存される初期条件のためにのみ時間的に補間します。したがって、これは気候学からの海洋ですが、時間的に一定の季節サイクルはありません。次のように作成されます。

```
ocean = SeasonalOceanClimatology(spectral_grid)
```

そして、海洋時間は `initialize!(model, time=time)` で設定されます。フィールドとオプションは次のとおりです。

  * `path::String`: [OPTION] 陸海マスクファイルを含むフォルダへのパス、パッケージパスのデフォルト
  * `file::String`: [OPTION] 海面温度のファイル名
  * `varname::String`: [OPTION] netcdfファイル内の変数名
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: [OPTION] 海面温度ファイルが存在するグリッド
  * `missing_value::Float64`: [OPTION] データ内の陸を表す欠損値
