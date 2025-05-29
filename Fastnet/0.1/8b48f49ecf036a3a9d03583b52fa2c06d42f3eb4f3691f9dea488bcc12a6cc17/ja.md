```
linkstate(net,kid)
linkstate_f(net,kid)
```

ネットワーク *net* におけるリンクの状態を、ID *kid* で返します。

リンクの状態は、FastNet コンストラクタに渡された順序で番号が付けられています。

この関数のすべてのバージョンは定数時間で実行されますが、fast (_f) バージョンはパフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

また、[nodestate!](#Fastnet.nodestate!)、[FastNet](#FastNet.FastNet) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,2),LinkType(1,1),LinkType(2,2)])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> lnk=makelink!(net,n1,n2);

julia> linkstate(net,lnk)
2
```
