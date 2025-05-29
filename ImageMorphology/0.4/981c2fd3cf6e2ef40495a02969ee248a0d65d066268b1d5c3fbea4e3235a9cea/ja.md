```
indices = component_indices([T], labeled_array)
```

入力されたラベル付き配列内の各ラベルのインデックスを取得します。`indices`は0ベースのインデックスベクトルにシフトされているため、背景ピクセルのインデックスは`indices[0]`になります。

オプションの型`T`は、インデックスの型を指定するために使用される`Int`/`IndexLinear()`または`CartesianIndex`/`IndexCartesian()`のいずれかです。デフォルトの選択は`IndexStyle(labeled_array)`です。

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

julia> indices = component_indices(label)
5-element OffsetArray(::Vector{Vector{Int64}}, 0:4) with eltype Vector{Int64} with indices 0:4:
 [8, 10, 17]
 [1, 6, 11, 16, 21]
 [2, 3, 4, 5, 7, 9, 12]
 [13, 14, 15, 19, 20, 24, 25]
 [18, 22, 23]

julia> indices = component_indices(CartesianIndex, label)
5-element OffsetArray(::Vector{Vector{CartesianIndex{2}}}, 0:4) with eltype Vector{CartesianIndex{2}} with indices 0:4:
 [CartesianIndex(3, 2), CartesianIndex(5, 2), CartesianIndex(2, 4)]
 [CartesianIndex(1, 1), CartesianIndex(1, 2), CartesianIndex(1, 3), CartesianIndex(1, 4), CartesianIndex(1, 5)]
 [CartesianIndex(2, 1), CartesianIndex(3, 1), CartesianIndex(4, 1), CartesianIndex(5, 1), CartesianIndex(2, 2), CartesianIndex(4, 2), CartesianIndex(2, 3)]
 [CartesianIndex(3, 3), CartesianIndex(4, 3), CartesianIndex(5, 3), CartesianIndex(4, 4), CartesianIndex(5, 4), CartesianIndex(4, 5), CartesianIndex(5, 5)]
 [CartesianIndex(3, 4), CartesianIndex(2, 5), CartesianIndex(3, 5)]
```

グレイ画像の場合、ラベルは[`label_components`](@ref)によって計算できます。
