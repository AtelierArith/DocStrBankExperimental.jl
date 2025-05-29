```
listnodes(FastNet)    
listnodes(FastNet,state)
```

FastNet *net* のすべてのノードのIDを返すか、*state* のすべてのノードを *net* から返します。

この関数の1引数メソッドは、ネットワーク内のすべてのノードのIDを含むベクトルを返します。2引数メソッドは、*state* のすべてのノードのベクトルを作成します。

関連情報として [listneighbors](#Fastnet.listneighbors) を参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(10,10,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,3,1)

julia> makenodes!(net,2,2)

julia> listnodes(net)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> listnodes(net,2)
2-element Vector{Int64}:
 4
 5
```
