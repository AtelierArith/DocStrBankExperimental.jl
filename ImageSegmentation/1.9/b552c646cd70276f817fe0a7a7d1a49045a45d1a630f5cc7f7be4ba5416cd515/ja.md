```
seg_img = seeded_region_growing(img, seeds, [kernel_dim], [diff_fn])
seg_img = seeded_region_growing(img, seeds, [neighbourhood], [diff_fn])
```

N-D画像`img`をシード付き領域成長アルゴリズムを使用してセグメント化し、セグメントに関する情報を含む[`SegmentedImage`](@ref)を返します。

# 引数:

  * `img`             :  セグメント化されるN-D画像（任意の軸が許可されます）
  * `seeds`           :  シードを含む`Vector`。各シードはCartesianIndex{N}とラベルのタプルです。ラベルに関する詳細は以下の注記を参照してください。
  * `kernel_dim`      :  （オプション）長さNの`Vector{Int}`または`NTuple{N,Int}`で、i番目の要素はN-直交近傍のi番目の辺の長さを表す奇数の正の整数です。
  * `neighbourhood`   :  （オプション）CartesianIndex{N}を入力として受け取り、その点の近傍を返す関数。
  * `diff_fn`         :  （オプション）領域の平均色と点の色との間の差異測定(δ)を返す関数。

!!! note
    点に付けられたラベルは正の整数でなければなりませんが、複数の点に同じラベルを割り当てることができます。出力には、入力画像と同じインデックスを持つラベル付き配列が含まれます。すべてのインデックスは、ラベルのいずれかまたは、アルゴリズムがそのインデックスを一意のラベルに割り当てられなかったことを示す特別なラベル'0'に割り当てられます。


# 例

```jldoctest; setup = :(using ImageCore, ImageMorphology,ImageSegmentation)
julia> img = zeros(Gray{N0f8},4,4);

julia> img[2:4,2:4] .= 1;

julia> seeds = [(CartesianIndex(3,1),1),(CartesianIndex(2,2),2)];

julia> seg = seeded_region_growing(img, seeds);

julia> labels_map(seg)
4×4 Matrix{Int64}:
 1  1  1  1
 1  2  2  2
 1  2  2  2
 1  2  2  2
```

# 引用:

Albert Mehnert, Paul Jackaway (1997), "An improved seeded region growing algorithm", Pattern Recognition Letters 18 (1997), 1065-1071
