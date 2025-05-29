```
group = getindex(g::Groups,groupname::AbstractString)
```

Return the NetCDF `group` with the name `groupname` from the parent group `g`.

For example:

```julia
ds = NCDataset("results.nc", "r");
forecast_group = ds.group["forecast"]
forecast_temp = forecast_group["temperature"]
```
