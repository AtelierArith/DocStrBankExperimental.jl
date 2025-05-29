物理パラメータ化の診断変数。

  * `nlat_half::Int64`
  * `ocean::SpeedyWeather.DynamicsVariablesOcean`
  * `land::SpeedyWeather.DynamicsVariablesLand`
  * `precip_large_scale::Any`: 大規模降水の累積 [m]
  * `precip_convection::Any`: 対流による降水の累積 [m]
  * `precip_rate_large_scale::Any`: 大規模降水のレート [m/s]、瞬時
  * `precip_rate_convection::Any`: 対流による降水のレート [m/s]、瞬時
  * `cloud_top::Any`: 雲の頂部 [m]
  * `sensible_heat_flux::Any`: 感覚熱フラックス [W/m²]、上向き
  * `evaporative_flux::Any`: 蒸発フラックス [kg/s/m^2]、上向き
  * `surface_shortwave_up::Any`: 表面放射: 短波上向き [W/m²]
  * `surface_shortwave_down::Any`: 表面放射: 短波下向き [W/m²]
  * `surface_longwave_up::Any`: 表面放射: 長波上向き [W/m²]
  * `surface_longwave_down::Any`: 表面放射: 長波下向き [W/m²]
  * `outgoing_shortwave_radiation::Any`: 出射短波放射 [W/m^2]
  * `outgoing_longwave_radiation::Any`: 出射長波放射 [W/m^2]
  * `albedo::Any`: アルベド [1]
  * `cos_zenith::Any`: 太陽天頂角のコサイン [1]
