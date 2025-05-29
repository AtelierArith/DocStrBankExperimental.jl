```
centroids = component_centroids(labeled_array)
```

入力されたラベル付き配列の各ラベルの重心を計算します。`centroids`は0ベースのインデックスベクトルにシフトされているため、背景ピクセルの重心は`centroids[0]`になります。

有限集合`X`の重心は、幾何学的中心とも呼ばれ、`sum(X)/length(X)`を使用して計算されます。ラベル`i`の重心を求めるために、ラベル`i`のピクセルのすべての（直交）インデックスが集合`X`を構築するために使用されます。

```jldoctest; setup=:(using ImageMorphology)
julia> A = [2 2 2 2 2; 1 1 1 0 1; 1 0 2 1 1; 1 1 2 2 2; 1 0 2 2 2]
5×5 Matrix{Int64}:
 2  2  2  2  2
 1  1  1  0  1
 1  0  2  1  1
 1  1  2  2  2
 1  0  2  2  2

julia> label = label_components(A) # four disjoint components
5×5 Matrix{Int64}:
 1  1  1  1  1
 2  2  2  0  4
 2  0  3  4  4
 2  2  3  3  3
 2  0  3  3  3

julia> component_centroids(label)
5-element OffsetArray(::Vector{Tuple{Float64, Float64}}, 0:4) with eltype Tuple{Float64, Float64} with indices 0:4:
 (3.3333333333333335, 2.6666666666666665)
 (1.0, 3.0)
 (3.142857142857143, 1.5714285714285714)
 (4.285714285714286, 3.857142857142857)
 (2.6666666666666665, 4.666666666666667)
```

グレイ画像の場合、ラベルは[`label_components`](@ref)によって計算できます。
