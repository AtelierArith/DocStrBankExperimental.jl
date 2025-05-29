```
dismantle_ci(g::AGraph, l::Integer, nrem; verbose=false)
```

参照文献 [1] の集合的影響 (CI) ヒューリスティックを距離パラメータ `l` (通常 `l=3,4`) で適用します。`g` から最大 `nrem` 頂点を削除し、結果のグラフの最大連結成分のサイズを最小化しようとします。最大CIがゼロになると、早めに停止します。

各イテレーションで情報を印刷するには、`verbose` を `true` に設定します。

戻り値は `(gnew, vmap, remlist)` で、`gnew` は縮小されたグラフ、`vmap` は `gnew` の頂点を古いものにマッピングする頂点マップ（[`rem_vertices!`](@ref) も参照）であり、`remlist` には削除された頂点が削除順に含まれます。

より詳細な制御については、[`dismantle_ci_init`](@ref) および [`dismantle_ci_oneiter!`](@ref) を参照してください。

**使用法**

```julia
g = Graph(100, 1000)
l=3
nrem=10
gnew, vmap, remlist = dismantle_ci(g, l, nrem)

# または同等の
gnew, heap, lneigs = dismantle_ci_init(g, l)

for it=1:nrem
    irem = dismantle_ci_oneiter!(gnew, heap, lneigs, l)
    irem <= 0 && break
    push!(remlist, irem)
    println("最大成分のサイズ: ", maximum(length, connected_components(g)))
end
vmap = rem_vertices!(gnew, remlist)
```

[1] Morone F., Makse H. 複雑ネットワークにおける最適浸透を通じた影響最大化。Nature (2015)
