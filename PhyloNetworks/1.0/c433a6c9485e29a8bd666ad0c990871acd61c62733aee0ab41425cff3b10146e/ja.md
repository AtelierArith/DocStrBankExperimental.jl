```
rootonedge!(HybridNetwork, edgeNumber::Integer; index::Bool=false)
rootonedge!(HybridNetwork, Edge)
```

ネットワーク/ツリーをエッジ番号 `edgeNumber` に沿って根付けします（デフォルトでは）または `index=true` の場合はインデックス `edgeNumber` で根付けします。属性 `ischild1` と `containroot` はその過程で更新されます。

これにより、ネットワークに新しいノードと新しいエッジが追加されます。興味のあるエッジを視覚化して特定するには、`plot(net, showedgenumber=true, showedgelength=false)` を使用してください。（パッケージ [PhyloPlots](https://github.com/juliaphylo/PhyloPlots.jl) を参照）

関連情報: [`rootatnode!`](@ref).
