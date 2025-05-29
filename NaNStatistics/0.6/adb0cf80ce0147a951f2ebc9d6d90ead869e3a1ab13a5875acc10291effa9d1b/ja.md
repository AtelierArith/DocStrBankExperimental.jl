```julia
histmean(counts, bincenters)
```

ヒストグラムで表されるデータの平均を推定します。これは、`bincenters`で中心が等間隔のビンに指定された`counts`として表されます。

## 例

```julia
julia> binedges = -10:0.01:10;

julia> counts = histcounts(randn(10000), binedges);

julia> bincenters = (binedges[1:end-1] + binedges[2:end])/2
-9.995:0.01:9.995

julia> histmean(counts, bincenters)
0.0039890000000003135
```
