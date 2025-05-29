```
linkcounts(net)
linkcounts_f(net)
```

さまざまなリンク状態におけるリンクの数を含む配列を返します。

配列の要素は、リンクタイプがFastNetコンストラクタに渡された順序と同じ順序でカウントを示します。

この関数に必要な時間は、リンク状態の数にのみ比例し（リンクの数には依存しません）、スケールします。

代替の（_f）バージョンのこの関数は、便利さのためにのみ提供されています。

[linkcounts](#Fastnet.countlinks)も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,2),LinkType(1,1),LinkType(2,2)])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);  

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,2);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n2,n3);

julia> makelink!(net,n3,n1);

julia> linkcounts(net)
3-element Vector{Int64}:
 2
 1
 0
```
