```
potential_radiation(datetime, lat, long)
potential_radiation(doy, hour, lat, long; timezone,year)
```

Compute potential radiation for given geolocation and time.

Because potential radiation does not change across years  (for a given location and daytime and day of year), time can be specified alternatively by doy and hour.

# Arguments

  * datetime:  UTC timestamp.
  * lat:       Latitude (decimal degrees)
  * long:      Longitude (decimal degrees)
  * doy:       day of year (integer starting from 1)
  * hour:      hour within the day (0.0 .. 24.0 float)

optional     

  * timezone:  Timezone for doy and hour, defaults to "GMT+x"  nearest to given longitude.
  * year: specific year for doy and hour
  * `...`: other keyword arguments passed to [`extraterrestrial_radiation`](@ref) such as `constants` and `FT`

# Value

vector of potential radiation (W m-2)

# Examples

```@example
# assume hours in the GMT+x that is closest to given longitude
potrad = potential_radiation(160, 10.5, 51.0, 11.5)
```
