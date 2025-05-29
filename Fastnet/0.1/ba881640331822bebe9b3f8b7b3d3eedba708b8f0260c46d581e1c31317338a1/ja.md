```
nodestate!(net,nid,s)
nodestate_f!(net,nid,s)
```

ネット *net* のノードID *nid* を *s* に設定します。

この関数の両方のバージョンの最悪のパフォーマンスは O(ks*k)+O(ns) であり、ここで ks は追跡されるリンク状態の数、k は影響を受けるノードの次数、ns はノード状態の数です。

高速 (_f) バージョンは、パフォーマンスを向上させるためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

また、[nodestate](#Fastnet.nodestate) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード数0、リンク数0のネットワーク

julia> randomgraph!(net)
ノード数1000、リンク数2000のネットワーク

julia> nodestate(net,1)
1

julia> nodestate!(net,1,2)

julia> nodestate(net,1)
2
```
