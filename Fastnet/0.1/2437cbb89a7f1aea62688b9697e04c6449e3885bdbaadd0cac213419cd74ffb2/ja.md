```
nullgraph!(net)
```

ネットワークからすべてのノードとリンクを削除します。

最初の引数 *net* はシミュレーションで使用されるFastNet構造体です。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,1,[])
ノード0およびリンク0のネットワーク

julia> randomgraph!(net)
ノード1000およびリンク2000のネットワーク

julia> nullgraph!(net)
ノード0およびリンク0のネットワーク
```
