```
specific_humidity_from_dewpoint(dewpoint_temperature, temperature, air_pressure, earth_param_set)
```

Estimates the specific humidity given the dewpoint temperature, temperature of the air in Kelvin, and air pressure in Pa, along with the ClimaLand earth*param*set. This is useful for creating the PrescribedAtmosphere - which needs specific humidity - from ERA5 reanalysis data.

We first compute the relative humidity using the Magnus formula, then the saturated vapor pressure, and then we compute q from vapor pressure and saturated vapor pressure.

For more information on the Magnus formula, see e.g. Lawrence, Mark G. (1 February 2005). "The Relationship between Relative Humidity and the Dewpoint Temperature in Moist Air: A Simple Conversion and Applications". Bulletin of the American Meteorological Society. 86 (2): 225–234.
