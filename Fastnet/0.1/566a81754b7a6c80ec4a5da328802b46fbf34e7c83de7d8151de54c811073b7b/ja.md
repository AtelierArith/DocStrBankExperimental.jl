```
indegree(net,nid)
indegree_f(net,nid)
```

ネットワーク *net* におけるノード *nid* の入次数を返します。

最悪のパフォーマンスは、影響を受けるノードの入次数にのみ依存します。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

また、[degree](#Fastnet.degree)、[outdegree](#Fastnet.outdegree) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ネットワークは0ノードと0リンクです

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n3,n2);

julia> indegree(net,n1)
0

julia> indegree(net,n2)
2
```
