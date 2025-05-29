```
seg_img = fast_scanning(img, threshold, [diff_fn])
```

N-D画像を高速スキャンアルゴリズムを使用してセグメント化し、セグメントに関する情報を含む[`SegmentedImage`](@ref)を返します。

# 引数:

  * `img`         : セグメント化されるN-D画像（任意の軸が許可されます）
  * `threshold`   : 同じセグメントと見なすための差分測定（δ）の上限；適応的しきい値処理のために、`img`と同じ次元数を持つ`AbstractArray`を渡すことができます
  * `diff_fn`     : （オプション）領域の平均色と点の色との間の差分測定（δ）を返す関数

# 例:

```jldoctest; setup = :(using ImageCore, ImageMorphology, ImageSegmentation)
julia> img = zeros(Float64, (3,3));

julia> img[2,:] .= 0.5;

julia> img[:,2] .= 0.6;

julia> seg = fast_scanning(img, 0.2);

julia> labels_map(seg)
3×3 Matrix{Int64}:
 1  4  5
 4  4  4
 3  4  6
```

# 引用:

Jian-Jiun Ding, Cheng-Jin Kuo, Wen-Chih Hong, "高速スキャンと適応的マージによる効率的な画像セグメンテーション技術"
