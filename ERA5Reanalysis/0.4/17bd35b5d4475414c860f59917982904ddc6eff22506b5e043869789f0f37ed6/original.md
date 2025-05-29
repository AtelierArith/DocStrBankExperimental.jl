```
ERA5Variable
```

Abstract supertype for ERA5 variables, with the following subtypes

```
SingleLevel   <: ERA5Variable
PressureLevel <: ERA5Variable
```

All `ERA5Variable` Types contain the following fields:

  * `ID` : The variable ID, that is also the identifier in the NetCDF files
  * `name` : The full-name of the variable
  * `long` : The variable long-name, which is used to specify retrievals from CDS
  * `dataset` : The full-name of the variable
  * `units` : The units of the variable

All `PressureLevel` Types contain the following fields:

  * `hPa` : The pressure level (in hPa) of the pressure-variable of interest
