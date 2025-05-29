```
degree(net,nid)
degree_f(net,nid)
```

ネットワーク *net* におけるノードの ID *nid* の次数を返します。

ここで次数は、このノードがリンクのエンドポイントとして現れる回数として解釈されるため、自己ループはそれがリンクするノードの次数に2を加えます。

最悪のケースのパフォーマンスは、影響を受けるノードの次数にのみスケールします。高速 (_f) バージョンは、より良いパフォーマンスのためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。

また、[indegree](#Fastnet.indegree)、[outdegree](#Fastnet.outdegree) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード数 0、リンク数 0 のネットワーク

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n2,n3);

julia> degree(net,n1)
1

julia> degree(net,n2)
2
```
