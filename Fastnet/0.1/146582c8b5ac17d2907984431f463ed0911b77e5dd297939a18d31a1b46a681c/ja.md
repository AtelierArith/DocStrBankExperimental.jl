```
destroylink!(net,kid)
destroylink_f!(net,kid)
```

ネットワーク *net* で ID *kid* のリンクを削除します。

この関数のすべてのバージョンは定数時間で実行されます。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。

また、[makelink!](#Fastnet.makelink!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ネットワークのノード数: 0、リンク数: 0

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,2);

julia> makelink!(net,n1,n2);

julia> net
ネットワークのノード数: 2、リンク数: 1

julia> lnk=randomlink(net);

julia> destroylink!(net,lnk)

julia> net
ネットワークのノード数: 2、リンク数: 0
```
