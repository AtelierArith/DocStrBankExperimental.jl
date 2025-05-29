```julia
nc_agg(
    f::AbstractString;
    ...
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}
nc_agg(
    f::AbstractString,
    fout;
    by,
    fun,
    outdir,
    overwrite,
    verbose
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}

```

# 引数

  * `f`: 入力ファイル
  * `fout`: 出力ファイル
  * `by`: "year" または "month"、または日付をグループ化するための関数

```julia
nc_agg(f; ...)
nc_agg(f, fout; by, fun, outdir, overwrite, verbose)
```

[`packages/NetCDFTools/QX4TD/src/utilize/nc_agg.jl:15`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/utilize/nc_agg.jl) で定義されています。

# 例

```
nc_agg(f, fout; by="year", fun=mean, outdir="./OUTPUT", overwrite=false, verbose=true)
```
