Frierson, 2007による簡略化されたBetts-Miller対流スキーム、https://doi.org/10.1175/JAS3935.1。これは彼らの論文におけるqref形式を実装しています。フィールドとオプションは次のとおりです。

  * `nlayers::Int64`: 垂直層の数
  * `time_scale::Dates.Second`: [OPTION] プロファイル調整のための緩和時間
  * `relative_humidity::Any`: [OPTION] 参照プロファイルの相対湿度
  * `surface_temp_humid::Any`: [OPTION] 湿潤擾乱を計算するための表面の温度、湿度
