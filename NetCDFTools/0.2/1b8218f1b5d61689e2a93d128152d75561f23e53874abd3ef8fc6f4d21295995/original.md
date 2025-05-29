```julia
nc_subset(
    f,
    range::Vector;
    ...
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}
nc_subset(
    f,
    range::Vector,
    fout;
    delta,
    check_vals,
    verbose,
    big,
    plevs,
    band,
    outdir,
    overwrite
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}

```

# Arguments

  * `check_vals`: If download failed, `length(unique(vals)) = 1`. Default check the length of data unique values

# Note

! 目前只保存其中一个变量

# Example

```julia
# 4-d array
url = "http://esgf3.dkrz.de/thredds/dodsC/cmip6/CMIP/CSIRO-ARCCSS/ACCESS-CM2/historical/r1i1p1f1/day/zg/gn/v20191108/zg_day_ACCESS-CM2_historical_r1i1p1f1_gn_19500101-19541231.nc"

nc_open(url)

# 3-d array
url = "http://esgf-data04.diasjp.net/thredds/dodsC/esg_dataroot/CMIP6/CMIP/CSIRO-ARCCSS/ACCESS-CM2/historical/r1i1p1f1/day/huss/gn/v20191108/huss_day_ACCESS-CM2_historical_r1i1p1f1_gn_18500101-18991231.nc"

range = [70, 140, 15, 55]
delta = 5

@time nc_subset(url, range)
```

```julia
nc_subset(f, range; ...)
nc_subset(
    f,
    range,
    fout;
    delta,
    check_vals,
    verbose,
    big,
    plevs,
    band,
    outdir,
    overwrite
)
```

defined at [`packages/NetCDFTools/QX4TD/src/utilize/nc_subset.jl:32`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/utilize/nc_subset.jl).
