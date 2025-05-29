```julia
histkurtosis(counts, bincenters)
```

ヒストグラムで表されるデータの過剰尖度[1]を推定します。これは、`counts`として指定された等間隔のビンの中心にある`bincenters`で表されます。

[1] Distributions.jlに従い、生の尖度ではなく過剰尖度を返します。過剰尖度は、尖度 - 3として定義され、正規分布は過剰尖度がゼロになります。

## 例

```julia
julia> binedges = -10:0.01:10;

julia> counts = histcounts(randn(10000), binedges);

julia> bincenters = (binedges[1:end-1] + binedges[2:end])/2
-9.995:0.01:9.995
t
julia> histkurtosis(counts, bincenters)
0.028863400305099596
```
