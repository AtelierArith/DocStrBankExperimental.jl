```
to_netcdf(data, dest::AbstractString; group::Symbol=:posterior, kwargs...)
to_netcdf(data, dest::NCDatasets.NCDataset; group::Symbol=:posterior)
```

`data`をNetCDFファイルに書き込みます。

`data`は[`InferenceData`](@ref)に変換できる任意の型であり、[`convert_to_inference_data`](@ref)を使用します。`InferenceData`でない場合、`group`はデータが表すグループを指定します。

`dest`はNetCDFファイルへのパスまたは開かれたNetCDFファイルを指定します。`dest`がパスの場合、残りの`kwargs`は[`NCDatasets.NCDataset`](https://alexander-barth.github.io/NCDatasets.jl/stable/dataset/#NCDatasets.NCDataset)に渡されます。

!!! note
    このメソッドを使用する前に、NCDatasetsがロードされている必要があります。


# 例

```julia
julia> using InferenceObjects, NCDatasets

julia> idata = from_namedtuple((; x = randn(4, 100, 3), z = randn(4, 100)))
InferenceData with groups:
  > posterior

julia> to_netcdf(idata, "data.nc")
"data.nc"
```
