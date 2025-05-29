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

# 引数

  * `check_vals`: ダウンロードに失敗した場合、`length(unique(vals)) = 1`。デフォルトではデータのユニークな値の長さをチェックします。

# 注意

! 目前只保存其中一个变量

# 例

```julia
# 4次元配列
url = "http://esgf3.dkrz.de/thredds/dodsC/cmip6/CMIP/CSIRO-ARCCSS/ACCESS-CM2/historical/r1i1p1f1/day/zg/gn/v20191108/zg_day_ACCESS-CM2_historical_r1i1p1f1_gn_19500101-19541231.nc"

nc_open(url)

# 3次元配列
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
