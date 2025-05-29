季節的な海洋気候学は、ファイルから月ごとの海面温度フィールドを読み取り、定期的に（デフォルトは3日ごと）時間的に補間して予測変数に保存します。フィールドとオプションは次のとおりです。

  * `nlat_half::Int64`: 一つの半球の緯度の数、赤道を含む
  * `path::String`: [OPTION] 海面温度を含むフォルダへのパス、パッケージパスのデフォルト
  * `file::String`: [OPTION] 海面温度のファイル名
  * `varname::String`: [OPTION] netcdfファイル内の変数名
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: [OPTION] 海面温度ファイルが存在するグリッド
  * `missing_value::Any`: [OPTION] データ内の陸地を表す欠損値
  * `monthly_temperature::Any`: グリッドに補間された月ごとの海面温度 [K]
