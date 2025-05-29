```
linksrc!(net,kid)
linksrc_f!(net,kid)
```

リンク *kid* のソースにあるノードのIDを *net* から返します。

この関数のすべてのバージョンは定数時間で実行されます。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。

また、[makelink!](#Fastnet.makelink!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード0とリンク0のネットワーク

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,2);

julia> k1=makelink!(net,n1,n2);

julia> linksrc(net,k1)==n1
true
```
