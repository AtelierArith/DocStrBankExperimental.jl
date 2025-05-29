```
filled_img = imfill(img::AbstractArray{Bool}, interval; dims=coords_spatial(img))
filled_img = imfill(img::AbstractArray{Bool}, interval, connectivity)
```

画像の連結成分はフラッドフィルアルゴリズムを使用して見つけられ、intervalの範囲にあるオブジェクトを埋めた後の元の画像のコピーを返します。オブジェクトを埋めるために、配列内の穴（埋める部分）を`true`で表現します。

パラメータ：

  * img            = 入力画像（ブール配列型）
  * interval       = この範囲内のサイズ（ボクセル数）のオブジェクトは`false`で埋められます
  * connectivity   = ブール値の接続パターン、[`label_components`](@ref)を参照してください。

# 例

```jldoctest; setup=:(using ImageMorphology)
julia> img = Bool[0 0 1 1 0 0;
                  0 1 0 1 1 0;
                  0 0 1 1 0 0]
3×6 Matrix{Bool}:
 0  0  1  1  0  0
 0  1  0  1  1  0
 0  0  1  1  0  0

julia> imfill(.!(img), 0:3)
3×6 BitMatrix:
 1  1  0  0  1  1
 1  0  0  0  0  1
 1  1  0  0  1  1

julia> .!(ans)
3×6 BitMatrix:
 0  0  1  1  0  0
 0  1  1  1  1  0
 0  0  1  1  0  0
```
