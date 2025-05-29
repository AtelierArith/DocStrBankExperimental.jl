meantemperature(temperatureminimum::ClimGrid, temperaturemaximum::ClimGrid)

Returns the daily mean temperature calculated from the maximum and minimum temperature. Daily maximum and minimum temperature must be in the same units. The mean temperature returned is in the same units as the daily minimum temperature and daily maximum temperature.

$Tmean = \frac{Tmax + Tmin}{2}$
