```
makelink!(net,src,dst)
makelink_f!(net,src,dst)
```

ネットワーク *net* でノード *src* からノード *dst* への新しいリンクを作成し、そのIDを返します。

この関数の両方のバージョンの最悪のパフォーマンスは、追跡されるリンク状態の数にのみ依存します。

高速 (_f) バージョンは、パフォーマンスを向上させるためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

また、[destroylink!](#Fastnet.destrolink!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> makelink!(net,n1,n2);

julia> net
Network of 2 nodes and 1 links
```
