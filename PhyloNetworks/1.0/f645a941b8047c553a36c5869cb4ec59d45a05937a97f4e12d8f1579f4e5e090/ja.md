```
nameinternalnodes!(net::HybridNetwork, prefix="i")
```

`net`内の名前がまだ付いていないノードに名前を追加します。葉ノードにはすでに名前が付いていますが、もし付いていなければ名前が付けられます。新しいノードの名前は「prefixk」の形式になります。ここで、`k`は整数です。したがって、デフォルトでは新しいノードの名前は「i1」、「i2」などの形式になります。

# 例

```jldoctest
julia> net = readnewick("((a:1,(b:1)#H1:1::0.8):5,(#H1:0::0.2,c:1):1);");

julia> nameinternalnodes!(net, "I") # デフォルトでは、内部ノード名なしで表示されます
HybridNetwork, Rooted Network
7 edges
7 nodes: 3 tips, 1 hybrid nodes, 3 internal tree nodes.
tip labels: a, b, c
((a:1.0,(b:1.0)#H1:1.0::0.8)I1:5.0,(#H1:0.0::0.2,c:1.0)I2:1.0)I3;

julia> writenewick(net; internallabel=false) # デフォルトでは、writenewickは内部名が存在する場合に表示します
"((a:1.0,(b:1.0)#H1:1.0::0.8):5.0,(#H1:0.0::0.2,c:1.0):1.0);"

julia> net = readnewick("((int5:1,(b:1)#H1:1::0.8):5,(#H1:0::0.2,c:1):1);"); # 一つの分類群名が「int」で始まります

julia> nameinternalnodes!(net, "int");

julia> writenewick(net)
"((int5:1.0,(b:1.0)#H1:1.0::0.8)int6:5.0,(#H1:0.0::0.2,c:1.0)int7:1.0)int8;"
```
