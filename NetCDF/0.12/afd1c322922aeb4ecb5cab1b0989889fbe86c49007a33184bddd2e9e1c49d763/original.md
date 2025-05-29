```
ncputatt(nc::String,varname::String,atts::Dict)
```

Writes the attributes defined in `atts` to the variable `varname` for the given NetCDF file name `nc`. Existing attributes are overwritten. If varname is not a valid variable name, a global attribute will be written.
