```
seg_img = unseeded_region_growing(img, threshold, [kernel_dim], [diff_fn])
seg_img = unseeded_region_growing(img, threshold, [neighbourhood], [diff_fn])
```

自動（未種付け）領域成長アルゴリズムを使用してN-D画像をセグメント化し、セグメントに関する情報を含む[`SegmentedImage`](@ref)を返します。

# 引数:

  * `img`             :  セグメント化されるN-D画像（任意の軸が許可されます）
  * `threshold`       :  ピクセルを同じセグメントと見なすための差異測定の上限（δ）
  * `kernel_dim`      :  （オプション）長さNの`Vector{Int}`または`NTuple{N,Int}`で、i番目の要素はN-直交近傍のi番目の辺の長さを表す奇数の正の整数
  * `neighbourhood`   :  （オプション）CartesianIndex{N}を入力として受け取り、その点の近傍を返す関数
  * `diff_fn`         :  （オプション）領域の平均色と点の色との間の差異測定（δ）を返す関数

# 例

```jldoctest; setup = :(using ImageCore, ImageMorphology, ImageSegmentation)
julia> img = zeros(Gray{N0f8},4,4);

julia> img[2:4,2:4] .= 1;

julia> seg = unseeded_region_growing(img, 0.2);

julia> labels_map(seg)
4×4 Matrix{Int64}:
 1  1  1  1
 1  2  2  2
 1  2  2  2
 1  2  2  2
```
