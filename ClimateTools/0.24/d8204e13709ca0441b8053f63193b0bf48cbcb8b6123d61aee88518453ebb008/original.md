wbgt(diurnal*temperature::ClimGrid, vapor*pressure::ClimGrid)

Returns the simplified wet-bulb global temperature (*wbgt*) (Celsius) calculated using the vapor pressure (Pa) of the day and the estimated mean diurnal temperature (Celsius; temperature between 7:00 (7am) and 17:00 (5pm)).

$wbgt = 0.567 * Tday + 0.00393 * vp + 3.94$
