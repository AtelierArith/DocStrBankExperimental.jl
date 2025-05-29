```
listneighbors(FastNet,nid)
```

ノード *nid* に隣接するすべてのノードのIDのベクトルを FastNet *net* から返します。

この関数はベクトルを割り当てる必要があるため、比較的遅くなります。あなたの *rates!* およびプロセス関数では、firstlinkout、firstlinkin、nexlinkout、nextlinkin を使用して隣接ノードを反復処理することが望ましいです。

関連情報として [listnodes](#Fastnet.listnodes) を参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(10,10,2,[])
ノード数0、リンク数0のネットワーク

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
