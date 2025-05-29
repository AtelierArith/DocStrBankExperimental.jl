```
unfame(fo::FameObject)
```

`FameObject`をJulia型に変換します。

  * 精度スカラー => `Float64`
  * 数値スカラー => `Float32`
  * 文字列スカラー => `String`
  * ブールスカラー => `Bool`
  * 名前リスト => `String` (形式は"{NAME1,NAME2,ETC}"、詳細はFameのヘルプを参照。)
  * 日付スカラー => [`MIT`](@ref TimeSeriesEcon.MIT) (CASEは`MIT{Unit}`になり、TimeSeriesEconでサポートされていない周波数は`ErrorException`をスローします)
  * 精度シリーズ => [`TSeries`](@ref TimeSeriesEcon.TSeries)
  * 数値シリーズ => [`TSeries`](@ref TimeSeriesEcon.TSeries) で要素型は`Float32`
  * ブールシリーズ => [`TSeries`](@ref TimeSeriesEcon.TSeries) で要素型は`Bool`
  * 日付シリーズ => [`TSeries`](@ref TimeSeriesEcon.TSeries) で要素型は[`MIT`](@ref TimeSeriesEcon.MIT)
  * 文字列シリーズ => `Vector{String}` (時系列メタデータは失われます)
