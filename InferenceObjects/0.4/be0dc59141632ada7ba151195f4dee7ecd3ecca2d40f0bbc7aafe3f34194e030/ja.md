```
from_netcdf(path::AbstractString; kwargs...) -> InferenceData
```

未開封のNetCDFファイルから[`InferenceData`](@ref)をロードします。

残りの`kwargs`は[`NCDatasets.NCDataset`](@extref)に渡されます。このメソッドはデータを即時にロードします。代わりに遅延ロードを行うには、開かれた`NCDataset`を`from_netcdf`に渡してください。

!!! note
    このメソッドを使用する前に、NCDatasetsがロードされている必要があります。


# 例

```julia
julia> using InferenceObjects, NCDatasets

julia> idata = from_netcdf("centered_eight.nc")
InferenceData with groups:
  > posterior
  > posterior_predictive
  > sample_stats
  > prior
  > observed_data
```

```
from_netcdf(ds::NCDatasets.NCDataset; load_mode) -> InferenceData
```

開かれたNetCDFファイルから[`InferenceData`](@ref)をロードします。

`load_mode`のデフォルトは`:lazy`で、変数をメモリに読み込むことを避けます。これらの配列に対する操作は遅くなります。`load_mode`は`:eager`にもでき、すべての変数をメモリにコピーします。この場合、`ds`を閉じることが安全です。`load_mode`が`:lazy`で、`InferenceData`を構築した後に`ds`が閉じられると、変数配列の使用は未定義の動作になります。

# 例

ウェブホストされたNetCDFファイルから`InferenceData`を遅延ロードする方法は次のとおりです。

```julia
julia> using HTTP, InferenceObjects, NCDatasets

julia> resp = HTTP.get("https://github.com/arviz-devs/arviz_example_data/blob/main/data/centered_eight.nc?raw=true");

julia> ds = NCDataset("centered_eight", "r"; memory = resp.body);

julia> idata = from_netcdf(ds)
InferenceData with groups:
  > posterior
  > posterior_predictive
  > sample_stats
  > prior
  > observed_data

julia> idata_copy = copy(idata); # ロードされたデータセットから切り離す

julia> close(ds);
```
