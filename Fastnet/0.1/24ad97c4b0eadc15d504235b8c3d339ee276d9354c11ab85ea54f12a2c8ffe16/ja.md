```
node(net,rp)
node(net,s,rp)
node_f(net,rp)
node_f(net,s,rp)
```

相対位置とノード状態からノードIDを決定します。

ノード関数は、特定の状態にあるノードの集合から、またはすべてのノードの集合からノードにアクセスする方法を提供します。2引数バージョンは、ネットワーク*net*内の位置*rp*にあるノードのIDを返します。3引数バージョンは、状態*s*にあるすべてのノード内の位置*rp*にあるノードのIDを返します。

この関数のすべてのバージョンは定数時間で実行されますが、高速(_f)バージョンはパフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については[基本概念](concepts.md)を参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード0およびリンク0のネットワーク

julia> randomgraph!(net)
ノード1000およびリンク2000のネットワーク

julia> nodestate!(net,123,2)

julia> nodestate!(net,345,2)

julia> node(net,2,1)
345

julia> node(net,2,2)
123

julia> node(net,1)
1

julia> destroynode!(net,1)

julia> node(net,1)
998
```
