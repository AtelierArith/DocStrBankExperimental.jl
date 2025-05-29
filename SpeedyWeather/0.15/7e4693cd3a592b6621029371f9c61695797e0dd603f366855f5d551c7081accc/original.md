Solar zenith angle varying with daily and seasonal cycle.

  * `length_of_day::Dates.Second`
  * `length_of_year::Dates.Second`
  * `equation_of_time::Bool`
  * `seasonal_cycle::Bool`
  * `solar_declination::SpeedyWeather.SinSolarDeclination{NF} where NF<:AbstractFloat`
  * `time_correction::SpeedyWeather.SolarTimeCorrection`
  * `initial_time::Base.RefValue{Dates.DateTime}`
