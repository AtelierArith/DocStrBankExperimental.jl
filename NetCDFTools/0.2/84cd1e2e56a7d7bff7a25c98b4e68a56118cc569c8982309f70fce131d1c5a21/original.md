```
ncdim_def(ds, name, val, attrib = Dict())
ncdim_def(ds, dim::NcDim)
ncdim_def(ds, dims::Vector{NcDim})
```

# Examples

```julia
## 1. by existing nc file
# f = "/mnt/j/Researches/Obs/Obs_ChinaHW_cluster/ncell_16/clusterId_HItasmax_movTRS_Obs.nc"
dims = nc_dims(f)
ds = nc_open("f2.nc", "c")
ncdim_def(ds, dims);
println(ds)
close(ds)

## 2. by assigned variables
# dates = nc_date(ds)
ds = nc_open("f3.nc", "c")
dim_t = NcDim_time(dates)
ncdim_def(ds, dim_t)
close(ds)
```
