```
removedegree2nodes!(net::HybridNetwork, keeproot::Bool=false)
```

`net`内の次数2のすべてのノードを削除し、毎回隣接する2つのエッジを融合させてネットワークを返します。ネットワークに次数2のルートがあり、`keeproot`がfalseの場合、ルートも削除され、ネットワークはルートなしになります。このルールの唯一の例外は、ルートが2つの（外向きの）ハイブリッドエッジに接続されている場合です。ルートを削除するとループエッジ（同じ端点）が残るため、元のネットワークのパスを保持するためにこれを避ける必要があります。この場合、`keeproot`がfalseであってもルートは保持されます。`keeproot`がtrueの場合、次数2であってもルートは保持されます。

[`fuseedgesat!`](@ref)を参照してください。

```jldoctest
julia> net = readnewick("(((((S1,(S2)#H1),(#H1,S3)))#H2),(#H2,S4));");

julia> PhyloNetworks.breakedge!(net.edge[3], net); # ハイブリッドエッジに沿って次数2のノードを作成

julia> PhyloNetworks.breakedge!(net.edge[3], net); # もう1つ：連続して2つ

julia> PhyloNetworks.breakedge!(net.edge[10], net); # 別の場所にもう1つ

julia> writenewick(net) # 余分な括弧のペア
"((#H2,S4),(((((S1,(((S2)#H1))),(#H1,S3)))#H2)));"

julia> removedegree2nodes!(net);

julia> writenewick(net) # ルートも消えた
"(#H2,S4,(((S1,(S2)#H1),(#H1,S3)))#H2);"

julia> net = readnewick("((((C:0.9)I1:0.1)I3:0.1,((A:1.0)I2:0.4)I3:0.6):1.4,(((B:0.2)H1:0.6)I2:0.5)I3:2.1);");

julia> removedegree2nodes!(net, true);

julia> writenewick(net, round=true) # ルートは保持された
"((C:1.1,A:2.0):1.4,B:3.4);"

```
