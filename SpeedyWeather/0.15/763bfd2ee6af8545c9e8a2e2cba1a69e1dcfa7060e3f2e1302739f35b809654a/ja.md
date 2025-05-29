Frierson, 2007による簡略化されたBetts-Miller対流スキーム、https://doi.org/10.1175/JAS3935.1 ですが、湿度はゼロに設定されています。フィールドとオプションは次のとおりです。

  * `nlayers::Int64`: 垂直層/レベルの数
  * `time_scale::Dates.Second`: [OPTION] プロファイル調整のための緩和時間
  * `surface_temp::Any`: [OPTION] 乾燥断熱を計算するための温度の表面摂動
