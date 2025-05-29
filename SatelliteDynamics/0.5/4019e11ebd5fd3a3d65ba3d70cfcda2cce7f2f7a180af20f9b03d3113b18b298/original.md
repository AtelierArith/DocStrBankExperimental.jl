Module-wide global SpaceWeatherData. This data object is used as the default source of geomagnetic data by dynamics models if no explicit  SpaceWeatherData file is provided to those transformations.

This value can be overridden in your own code as follows:

```julia
SatelliteDynamics.SpaceWeather.SPACE_WEATHER_DATA = SpaceWeatherData(index_file)
```

This global variable defaults used are pull from the Celestrak Space Weather data repository: https://celestrak.org/SpaceData/
