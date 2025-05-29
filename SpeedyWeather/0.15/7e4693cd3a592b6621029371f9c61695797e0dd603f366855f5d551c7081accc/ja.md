太陽天頂角は日々および季節のサイクルに応じて変化します。

  * `length_of_day::Dates.Second`
  * `length_of_year::Dates.Second`
  * `equation_of_time::Bool`
  * `seasonal_cycle::Bool`
  * `solar_declination::SpeedyWeather.SinSolarDeclination{NF} where NF<:AbstractFloat`
  * `time_correction::SpeedyWeather.SolarTimeCorrection`
  * `initial_time::Base.RefValue{Dates.DateTime}`
