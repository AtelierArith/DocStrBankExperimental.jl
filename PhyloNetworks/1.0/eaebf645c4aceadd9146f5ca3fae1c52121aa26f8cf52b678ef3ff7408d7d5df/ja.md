```
rotate!(net::HybridNetwork, nodeNumber::Integer; orderedEdgeNum::Array{Int,1})
```

ノードの子エッジの順序を回転させます。交差するエッジを取り除くためにプロットに便利です。`node`が多重分岐のない木のノードである場合、2つの子エッジが入れ替えられ、オプション引数`orderedEdgeNum`は無視されます。

ノードとエッジの番号をネットワーク上にマッピングするには、`plot(net, shownodenumber=true, showedgenumber=false)`を使用します。以下の例に示すように。（パッケージ[PhyloPlots](https://github.com/juliaphylo/PhyloPlots.jl)を参照）

警告: エッジが正しく指向されていることを前提としています（ischild1が更新されます）。これは`plot(net)`によって行われます。そうでない場合は`directedges!(net)`を実行してください。

# 例

```julia
julia> net = readnewick("(A:1.0,((B:1.1,#H1:0.2::0.2):1.2,(((C:0.52,(E:0.5)#H2:0.02::0.7):0.6,(#H2:0.01::0.3,F:0.7):0.8):0.9,(D:0.8)#H1:0.3::0.8):1.3):0.7):0.1;");
julia> using PhyloPlots
julia> plot(net, shownodenumber=true)
julia> rotate!(net, -4)
julia> plot(net)
julia> net=readnewick("(4,((1,(2)#H7:::0.864):2.069,(6,5):3.423):0.265,(3,#H7:::0.136):10.0);");
julia> plot(net, shownodenumber=true, showedgenumber=true)
julia> rotate!(net, -1, orderedEdgeNum=[1,12,9])
julia> plot(net, shownodenumber=true, showedgenumber=true)
julia> rotate!(net, -3)
julia> plot(net)
```

`LinearAlgebra`もJulia v1.5で`rotate!`という名前の関数をエクスポートしています。Julia v1.5以降で両方のパッケージを使用する必要がある場合、`rotate!`の使用は`PhyloNetworks.rotate!`のように修飾する必要があります。
