```
destroynode!(net,nid)
destroynode_f!(net,nid)
```

ネットワーク *net* から ID *nid* のノードを削除します。

この関数の両方のバージョンの最悪のパフォーマンスは O(ks*k)+O(ns) であり、ここで ks は追跡されているリンク状態の数、k は影響を受けるノードの次数、ns はノード状態の数です。

高速 (_f) バージョンは、パフォーマンスを向上させるためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

また、[makenode!](#Fastnet.makenode!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード数 0、リンク数 0 のネットワーク

julia> n=makenode!(net,1);

julia> net
ノード数 1、リンク数 0 のネットワーク

julia> destroynode!(net,n)

julia> net
ノード数 0、リンク数 0 のネットワーク
```
