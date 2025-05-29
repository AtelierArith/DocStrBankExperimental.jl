```
nextlinkin!(net,kid)
nextlinkin_f!(net,kid)
```

リンク *kid* の宛先にあるノードへの次の受信リンクのIDを取得します。

この関数は、ノードの受信リンクを反復処理するために使用できます。 *kid* がノードの最後のリンクである場合、返り値はゼロになります。

この関数のすべてのバージョンは定数時間で実行されます。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。

また、[firstlinkin](#Fastnet.firstlinkin)、[nextlinkout](#Fastnet.nextlinkout) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> n4=makenode!(net,1);

julia> makelink!(net,n2,n1)
1

julia> makelink!(net,n3,n1)
2

julia> makelink!(net,n4,n1)
3

julia> k=firstlinkin(net,n1);

julia> while k!=0
           println(k)
           k=nextlinkin(net,k)
           end
3
2
1
```
