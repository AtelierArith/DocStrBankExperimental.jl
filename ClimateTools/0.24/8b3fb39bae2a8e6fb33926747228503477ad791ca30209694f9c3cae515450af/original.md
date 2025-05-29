diurnaltemperature(temperatureminimum::ClimGrid, temperaturemaximum::ClimGrid, α::Float64)

Returns an estimation of the diurnal temperature (temperature between 7:00 (7am) and 17:00 (5pm)). The estimation is a linear combination of the daily minimum temperature (temperatureminimum) and daily maximum temperature (temperaturemaximum). The value of α has to be estimated seperatly from observations and depends on the location. The daily max and min must be in the same unit and in Celsius or Kelvin The diurnal temperature returned is in the same units as the daily minimum temperature and daily maximum temperature.

$Tdiu = α * Tmin + (1 - α) * Tmax$
