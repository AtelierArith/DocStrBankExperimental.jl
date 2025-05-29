```
avert_emissions_profiles(; avert_region_abbr::String="", latitude::Real, longitude::Real, time_steps_per_hour::Int=1, load_year::Int=2017, avert_data_year::Int=2023)
```

This function gets CO2, NOx, SO2, and PM2.5 grid emission rate profiles (1-year time series) from the AVERT dataset.     If avert*region*abbr is supplied, this will overwrite the default region that would otherwise be selected using the lat, long. Returned emissions profile is adjusted for day of week alignment with load_year.

This function is used for the /emissions_profile endpoint in the REopt API, in particular      for the webtool to display grid emissions defaults before running REopt,      but is also generally an external way to access AVERT data without running REopt.
