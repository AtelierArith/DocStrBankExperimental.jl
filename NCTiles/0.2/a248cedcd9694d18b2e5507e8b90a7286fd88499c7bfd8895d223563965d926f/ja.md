```
createfile(filename, field::Union{NCvar,Dict{String,NCvar}}, README;
            fillval=NaN, missval=NaN, itile=1, ntile=1)
```

NetCDFファイルを作成し、`NCDatasets.jl`または`NetCDF.jl`を使用して変数と次元の定義を追加します。
