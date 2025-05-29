```
SingleVariable(
    ST = String;
    ID :: AbstractString,
    long :: AbstractString = "",
    name :: AbstractString,
    units :: AbstractString
) -> evar :: SingleLevel
```

Create a custom Single-Level variable that is not in the default list exported by ERA5Reanalysis.jl.  These variables are not available in the CDS store, and so they must be separately calculated from other variables and analyzed.

# Keyword Arguments

  * `ID` : variable ID (in string format) used in the NetCDF file
  * `long` : long-name for variable (used in specifying variable for CDS downloads)
  * `name` : user-defined variable name
  * `units` : user-defined units of the variable
  * `inCDS` : Boolean that indicates if this variable is available on the CDS store.  True if available.
