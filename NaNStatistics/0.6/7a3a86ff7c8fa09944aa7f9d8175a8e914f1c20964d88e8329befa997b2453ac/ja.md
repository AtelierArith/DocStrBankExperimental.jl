```julia
histvar(counts, bincenters; corrected::Bool=true)
```

ヒストグラムで表されるデータの分散を推定します。これは、`bincenters`で中心が等間隔のビンに指定された`counts`として表されます。

`counts`が正規化されている場合、またはデータセットのカウントを表すヒストグラムではなくPDFの解析的推定を表す場合、分散に対するベッセルの補正は行わない方が良いでしょう。つまり、`corrected`キーワード引数を`false`に設定します。

## 例

```julia
julia> binedges = -10:0.01:10;

julia> counts = histcounts(randn(10000), binedges);

julia> bincenters = (binedges[1:end-1] + binedges[2:end])/2
-9.995:0.01:9.995
t
julia> histvar(counts, bincenters)
0.9991854064196424
```
