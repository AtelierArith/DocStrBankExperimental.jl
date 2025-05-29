```
makenode!(net,s)
makenode_f!(net,s)
```

ネットワーク *net* に状態 *s* の新しいノードを作成し、そのIDを返します。

この関数の両方のバージョンの最悪のパフォーマンスは、ノードの状態の数にのみ比例します。

高速 (_f) バージョンは、パフォーマンスを向上させるためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

また、[destroynode!](#Fastnet.destroynode!)、[makenodes!](#Fastnet.makenodes!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード0個、リンク0個のネットワーク

julia> makenode!(net,2)
1

julia> net
ノード1個、リンク0個のネットワーク

julia> nodestate(net,1)
2
```
