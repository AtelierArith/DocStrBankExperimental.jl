LeeとKimによって定義された対流加熱、2003年、JASは対流パラメータ化として実装されています。フィールドは次のとおりです。

  * `nlat::Int64`
  * `time_scale::Dates.Second`: [OPTION] Q*最大加熱強度を1K/時間*スケールとして
  * `p₀::Any`: [OPTION] 最大加熱の圧力 [hPa]
  * `σₚ::Any`: [OPTION] 加熱の垂直範囲 [hPa]
  * `θ₀::Any`: [OPTION] 加熱の緯度 [˚N]
  * `σθ::Any`: [OPTION] 加熱の緯度幅 [˚]
  * `lat_mask::Vector`
