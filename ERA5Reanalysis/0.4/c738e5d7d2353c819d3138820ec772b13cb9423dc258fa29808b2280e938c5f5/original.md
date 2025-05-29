```
PressureVariable(
    ST = String;
    ID :: AbstractString,
    long :: AbstractString = "",
    name :: AbstractString,
    units :: AbstractString,
    hPa   :: Int = 0,
    throw :: Bool = true
) -> evar :: PressureCustom
```

Create a custom Pressure-Level variable that is not in the default list exported by ERA5Reanalysis.jl.  These variables are not available in the CDS store, and so they must be separately calculated from other variables and analyzed.

# Keyword Arguments

  * `ID` : variable ID (in string format) used in the NetCDF file
  * `long` : long-name for variable (used in specifying variable for CDS downloads)
  * `name` : user-defined variable name
  * `units` : user-defined units of the variable
  * `hPa`   : Pressure level specified in hPa. Default is 0, which indicates all levels.
  * `throw` : if `hPa` level does not exist and `throw` is true, throw error, otherwise find nearest pressure level
