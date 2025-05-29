```
nodecounts(net)
nodecounts_f(net)
```

さまざまなノード状態におけるノードの数を含む配列を返します。

この関数に必要な時間はノード状態の数にのみ依存し、ノードの数には依存しません。

この関数の代替 (_f) バージョンは nodecounts と同一であり、便利さのために提供されています。

[countnodes](#Fastnet.countnodes) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノードが 0 のリンクが 0 のネットワーク

julia> randomgraph!(net)
ノードが 1000 のリンクが 2000 のネットワーク

julia> for i=1:20
         n=node(net,1,1)
         nodestate!(net,n,2)
       end

julia> nodecounts(net)
2-element Vector{Int64}:
 980
  20
```
