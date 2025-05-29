```
listlinks(net)
```

*net* のすべてのリンクのソースとデスティネーションを含む配列を返します。

返り値は次元 (K,3) の二次元配列で、K はネットワーク内のリンクの数です。各行は1つのリンクに対応します。配列の内容は次のとおりです。

  * 第一列: 各リンクのリンクIDと同じ
  * 第二列: リンクのソースノード
  * 第三列: リンクのデスティネーションノード

警告: 行インデックスがリンクIDと同じであることに依存しないでください。

[リンクリストを保存する](#Fastnet.savelinklist) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ネットワークのノード数: 0、リンク数: 0

julia> makenodes!(net,5,1)

julia> makelink!(net,1,2)
1

julia> makelink!(net,1,3)
2

julia> net=FastNet(1000,2000,2,[])
ネットワークのノード数: 0、リンク数: 0

julia> makenodes!(net,5,1)

julia> makelink!(net,1,2)
1

julia> makelink!(net,2,3)
2

julia> makelink!(net,3,4)
3

julia> makelink!(net,4,5)
4

julia> makelink!(net,5,1)
5

julia> listlinks(net)
5×3 Matrix{Int64}:
 1  1  2
 2  2  3
 3  3  4
 4  4  5
 5  5  1
```
