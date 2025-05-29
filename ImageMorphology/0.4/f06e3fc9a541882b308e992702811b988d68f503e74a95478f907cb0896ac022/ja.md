```
boxes = component_boxes(labeled_array)
```

各ラベルの最小バウンディングボックスを計算します。背景ラベルも含まれます。ラベルは[`label_components`](@ref)によって計算できます。

各バウンディングボックスは`CartesianIndices`として表されます。`boxes`は0ベースのインデックスベクトルにシフトされているため、背景領域は`boxes[0]`です。

```jldoctest; setup=:(using ImageMorphology)
julia> A = [2 2 2 2 2; 1 1 1 0 1; 1 0 2 1 1; 1 1 2 2 2; 1 0 2 2 2]
5×5 Matrix{Int64}:
 2  2  2  2  2
 1  1  1  0  1
 1  0  2  1  1
 1  1  2  2  2
 1  0  2  2  2

julia> label = label_components(A) # 四つの非連結成分
5×5 Matrix{Int64}:
 1  1  1  1  1
 2  2  2  0  4
 2  0  3  4  4
 2  2  3  3  3
 2  0  3  3  3

julia> boxes = component_boxes(label) # すべての領域のバウンディングボックスを取得
5-element OffsetArray(::Vector{CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}}, 0:4) with eltype CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}} with indices 0:4:
 CartesianIndices((2:5, 2:4))
 CartesianIndices((1:1, 1:5))
 CartesianIndices((2:5, 1:3))
 CartesianIndices((3:5, 3:5))
 CartesianIndices((2:3, 4:5))

julia> A[boxes[1]] # ラベル1の画像領域をクロップ
1×5 Matrix{Int64}:
 2  2  2  2  2

julia> A[boxes[4]] # ラベル4の画像領域をクロップ
2×2 Matrix{Int64}:
 0  1
 1  1
```
