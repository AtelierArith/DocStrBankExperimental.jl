```
counts = component_lengths(labeled_array)
```

入力されたラベル付き配列内の各ラベルの数をカウントします。`counts`は0ベースのインデックスベクトルにシフトされているため、背景ピクセルの数は`counts[0]`になります。

```jldoctest; setup=:(using ImageMorphology)
julia> A = [2 2 2 2 2; 1 1 1 0 1; 1 0 2 1 1; 1 1 2 2 2; 1 0 2 2 2]
5×5 Matrix{Int64}:
 2  2  2  2  2
 1  1  1  0  1
 1  0  2  1  1
 1  1  2  2  2
 1  0  2  2  2

julia> label = label_components(A) # 四つの離散コンポーネント
5×5 Matrix{Int64}:
 1  1  1  1  1
 2  2  2  0  4
 2  0  3  4  4
 2  2  3  3  3
 2  0  3  3  3

julia> component_lengths(label)
5-element OffsetArray(::Vector{Int64}, 0:4) with eltype Int64 with indices 0:4:
 3
 5
 7
 7
 3
```

グレイ画像の場合、ラベルは[`label_components`](@ref)によって計算できます。
