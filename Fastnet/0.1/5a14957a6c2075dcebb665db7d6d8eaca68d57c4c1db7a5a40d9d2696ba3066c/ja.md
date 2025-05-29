```
nodestate(net,nid)
nodestate_f(net,nid)
```

ネットワーク *net* のノード ID *nid* の状態を返します。

この関数のすべてのバージョンは定数時間で実行されますが、fast (_f) バージョンはパフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。

また、[nodestate!](#Fastnet.nodestate!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード数 0、リンク数 0 のネットワーク

julia> randomgraph!(net)
ノード数 1000、リンク数 2000 のネットワーク

julia> nodestate(net,1)
1

julia> nodestate!(net,1,2)

julia> nodestate(net,1)
2
```
