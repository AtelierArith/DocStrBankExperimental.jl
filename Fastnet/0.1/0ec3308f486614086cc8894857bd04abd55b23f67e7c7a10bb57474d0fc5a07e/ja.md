```
showlinks(net)
```

FastNet *net* のすべてのリンクに関する情報を表示します。

この関数は主にテスト/デバッグ用に意図されています。リンクが少ないネットワークでのみ使用してください。

他にも [shownodes](#Fastnet.shownodes) を参照してください。

# 例

```jldoctest julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,1),LinkType(1,2),LinkType(2,2)]);

julia> makenodes!(net,5,1)

julia> makenodes!(net,5,2)

julia> makelink!(net,node(net,1,1),node(net,1,2)); 1

julia> makelink!(net,node(net,1,1),node(net,2,1)) 2

julia> makelink!(net,node(net,2,1),node(net,2,2)) 3

julia> makelink!(net,node(net,2,2),node(net,1,2)) 4

julia> showlinks(net) id      src     dest    state 1       1       2       1 2       1       6       2 3       6       7       3 4       7       2       2 
```
