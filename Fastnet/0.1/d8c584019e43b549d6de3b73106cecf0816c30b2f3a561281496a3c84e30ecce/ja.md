```
listnodestates(net)
```

*net*内のすべてのノードのIDと状態を含む配列を返します。

返される値は次元(K,2)の二次元配列であり、Kはネットワーク内のノードの数です。各行は1つのノードに対応します。配列の内容は次のとおりです。

  * 第一列: 対応するノードのID
  * 第二列: ノードの状態

警告: 行インデックスがノードIDと同じであることに依存しないでください。

関連情報: [listlinks](#Fastnet.listlinks) 

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(100,100,3,[])
ノード0個、リンク0個のネットワーク

julia> makenodes!(net,2,1)

julia> makenodes!(net,2,2)

julia> makenodes!(net,3,3)

julia> listnodestates(net)
7×2 Matrix{Int64}:
 1  1
 2  1
 3  2
 4  2
 5  3
 6  3
 7  3
```
