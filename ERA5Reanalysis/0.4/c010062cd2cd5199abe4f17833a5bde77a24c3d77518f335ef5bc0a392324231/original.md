```
PressureVariable(
    ID :: AbstractString,
    ST = String;
    hPa   :: Int = 0
    throw :: Bool = true
) -> evar :: SingleLevel
```

Retrieve the basic properties of the Pressure-Level variable defined by `ID` at pressure-height indicated by `hPa` and put them in the `evar` SingleLevel type structure.

# Arguments

  * `ID` : variable ID (in string format) used in the NetCDF file

# Keyword Arguments

  * `hPa` : Integer specifying pressure-level height in hPa
  * `throw` : if `hPa` level does not exist and `throw` is true, throw error, otherwise find nearest pressure level
