```
group = getindex(g::Groups,groupname::AbstractString)
```

親グループ `g` から名前 `groupname` の NetCDF `group` を返します。

例えば：

```julia
ds = NCDataset("results.nc", "r");
forecast_group = ds.group["forecast"]
forecast_temp = forecast_group["temperature"]
```
