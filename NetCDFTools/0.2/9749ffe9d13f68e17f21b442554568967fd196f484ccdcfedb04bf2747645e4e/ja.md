```julia
nc_agg_dir(indir; by, replacement, outdir, kw...)

```

# 例

```julia-repl
scenario = "historical"
indir = "Z:/ChinaHW/CMIP6_cluster_HItasmax_adjchunk/HI_tasmax/historical"
outdir = "Z:/ChinaHW/CMIP6_cluster_HItasmax_adjchunk/HI_tasmax_year/historical"

nc_agg_dir(indir; by="year", replacement="day"=>"year", outdir)
```

```julia
nc_agg_dir(indir; by, replacement, outdir, kw...)
```

[`packages/NetCDFTools/QX4TD/src/utilize/nc_agg.jl:69`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/utilize/nc_agg.jl) で定義されています。
