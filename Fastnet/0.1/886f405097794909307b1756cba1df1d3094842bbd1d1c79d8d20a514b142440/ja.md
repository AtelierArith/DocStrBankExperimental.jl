```
firstlinkin(net,nid)
firstlinkin_f(net,nid)
```

ノードID *nid* の最初の受信リンクのリンクIDをネットワーク *net* から返します。

受信リンクがない場合、返り値は0です。

この関数のすべてのバージョンは定数時間で実行されます。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。

また、[firstlinkout](#Fastnet.firstlinkout)、[nextlinkin](#Fastnet.nextlinkin) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード0およびリンク0のネットワーク

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> l1=makelink!(net,n1,n2);

julia> firstlink=firstlinkin(net,n2);

julia> firstlink==l1
true

julia> linksrc(net,firstlink)==n1
true

julia> linkdst(net,firstlink)==n2
true
```
