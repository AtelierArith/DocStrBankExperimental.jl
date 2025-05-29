```
OpenMeteo()
OpenMeteo(
    vars=PlantMeteo.DEFAULT_OPENMETEO_HOURLY,
    forecast_server="https://api.open-meteo.com/v1/forecast",
    historical_server="https://archive-api.open-meteo.com/v1/era5",
    units=OpenMeteoUnits(),
    timezone="UTC",
    models=["auto"]
)
```

A type that defines the [open-meteo.com](https://open-meteo.com/) API.  No need of an API key as it is free. Please keep in mind that the API is distributed under the AGPL license, that it is not free for commercial use, and that you should use it responsibly.

# Notes

The API wrapper provided by PlantMeteo is only working for the hourly data as daily data is missing  some variables. The API wrapper is also not working for the "soil" variables as they are not consistant between forecast and historical data.

# See also

[`to_daily`](@ref)

# Arguments

  * `vars`: the variables needed, see [here](https://open-meteo.com/en/docs).
  * `forecast_server`: the server to use for the forecast, see

[here](https://open-meteo.com/en/docs). Default to `https://api.open-meteo.com/v1/forecast`.

  * `historical_server`: the server to use for the historical data, see

[here](https://open-meteo.com/en/docs). Default to `https://archive-api.open-meteo.com/v1/era5`.

  * `start_archive::Dates.Day`: the first day on which we have to get data from the historical archive instead of the forecast server,

data is at 25km resolution in the archive. Default to -150 days.

  * `units::OpenMeteoUnits`: the units used for the variables, see [`OpenMeteoUnits`](@ref).
  * `timezone`: the timezone used for the data, see [the list here](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

Default to "UTC". This parameter is not checked, so be careful when using it.

  * `models`: the models to use for the forecast. Default to `"["best_match"]"`. See [`OPENMETEO_MODELS`](@ref) for more details.

# Troubleshooting

If you get an error when calling the API, try to decrease the value of `start_archive` to *e.g.*. 100 days before  today (`-Dates.Day(100)`).

# Details

The default variables are: "temperature*2m", "relativehumidity*2m", "precipitation", "surface*pressure", "windspeed*10m", "shortwave*radiation", "direct*radiation", "diffuse_radiation".

Note that we don't download: "soil*temperature*0cm", "soil*temperature*6cm", "soil*temperature*18cm", "soil*temperature*54cm", "soil*moisture*0*1cm", "soil*moisture*1*3cm", "soil*moisture*3*9cm", "soil*moisture*9*27cm" and "soil*moisture*27_81cm"  by default as they are not consistant between forecast and hystorical data.

# Sources

  * [Open-Meteo.com](https://open-meteo.com/), under Attribution

4.0 International (CC BY 4.0).

  * Copernicus Climate Change Service information 2022 (Hersbach et al., 2018).

Hersbach, H., Bell, B., Berrisford, P., Biavati, G., Horányi, A., Muñoz Sabater, J., Nicolas, J.,  Peubey, C., Radu, R., Rozum, I., Schepers, D., Simmons, A., Soci, C., Dee, D., Thépaut, J-N. (2018):  ERA5 hourly data on single levels from 1959 to present.  Copernicus Climate Change Service (C3S) Climate Data Store (CDS). (Updated daily), 10.24381/cds.adbb2d47
