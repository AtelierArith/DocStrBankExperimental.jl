```
nextlinkout!(net,kid)
nextlinkout_f!(net,kid)
```

ノード *kid* のリンクのソースであるノードからの次の出力リンクのIDを取得します。

この関数は、ノードの出力リンクを反復処理するために使用できます。 *kid* がノードの最後のリンクである場合、返り値はゼロになります。

この関数のすべてのバージョンは定数時間で実行されます。高速 (_f) バージョンは、パフォーマンスを向上させるためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。

また、[firstlinkout](#Fastnet.firstlinkout)、[nextlinkin](#Fastnet.nextlinkin) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード数0、リンク数0のネットワーク

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,1);

julia> n4=makenode!(net,1);

julia> makelink!(net,n1,n2)
1

julia> makelink!(net,n1,n3)
2

julia> makelink!(net,n1,n4)
3

julia> k=firstlinkout(net,n1);

julia> while k!=0
           println(k)
           k=nextlinkout(net,k)
           end
3
2
1
```
