```
nodeexists(net,nid)
nodeexists_f(net,nid)
```

*nid*というIDを持つノードが*net*に存在するかどうかを返します。存在しない場合はfalseを返します。

この関数は定数時間で実行されます。高速(_f)バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については[基本概念](concepts.md)を参照してください。

また、[makenode!](#Fastnet.makenode!)、[destroynode!](#Fastnet.destroynode!)も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> nodeexists(net,n1)
true
```
