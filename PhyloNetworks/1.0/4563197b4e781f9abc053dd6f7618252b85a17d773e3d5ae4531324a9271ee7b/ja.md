```
rootatnode!(HybridNetwork, nodeNumber::Integer; index::Bool=false)
rootatnode!(HybridNetwork, Node)
rootatnode!(HybridNetwork, nodeName::AbstractString)
```

ネットワーク/ツリーオブジェクトを、名前 'nodeName' または番号 'nodeNumber' のノードで根付けます（デフォルトでは）または、index=true の場合はインデックス 'nodeNumber' で根付けます。属性 ischild1 と containroot はその過程で更新されます。興味のあるノードを視覚化して特定するには、`plot(net, shownodenumber=true, showedgelength=false)` を使用してください。（パッケージ [PhyloPlots](https://github.com/juliaphylo/PhyloPlots.jl) を参照）

ネットワークを返します。

警告:

  * ノードが葉である場合、根は葉に隣接するエッジに配置されます。これにより新しいノードが追加される可能性があります。
  * 希望する根の配置が1つ以上のハイブリッドと互換性がない場合、

      * 元のネットワークは古い根とエッジの方向で復元されます。
      * RootMismatch エラーがスローされます。

参照: [`rootonedge!`](@ref).
