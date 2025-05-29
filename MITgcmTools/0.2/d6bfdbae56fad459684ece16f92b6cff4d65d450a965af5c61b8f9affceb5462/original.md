```
read_mnc(pth::String,fil::String,var::String)
```

Read variable `var` from a set of `MITgcm` MNC-type files (netcdf files), combine, and return as an Array. This method will search within `pth` for files that start with `fil`.
