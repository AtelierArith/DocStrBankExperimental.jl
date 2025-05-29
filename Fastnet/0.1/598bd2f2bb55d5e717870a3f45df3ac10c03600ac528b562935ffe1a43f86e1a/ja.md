```
outdegree(net,nid)
outdegree_f(net,nid)
```

ネットワーク *net* のノード ID *nid* の出次数を返します。

最悪のケースのパフォーマンスは、影響を受けるノードの出次数のみに比例します。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

また、[degree](#Fastnet.degree)、[indegree](#Fastnet.indegree) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード数 0、リンク数 0 のネットワーク

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n3,n2);

julia> outdegree(net,n1)
1

julia> outdegree(net,n2)
0
```
