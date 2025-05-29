```
cube_label(pointdim::Int, pointlen::Int, pointinfo::Vector{Int})
```

キューブの座標情報からラベルを作成します。

周囲のユークリッド空間の次元は `pointdim` であり、各座標のフィールド長は `pointlen` です。ベクトル `pointinfo` は少なくとも `pointdim` の2倍の長さでなければなりません。最初の `pointdim` のエントリにはアンカーポイントの座標が含まれ、次の `pointdim` のエントリは区間のサイズに応じて0または1です。例えば、`poindim = 3` で `pointinfo = [1,2,3,1,0,1]` の場合、`[1,2] x [2] x [3 4]` で与えられる三次元空間内のキューブを表現します。

# 例

```jldoctest
julia> cube_label(3,2,[10,23,5,1,1,0])
"102305.110"
```
