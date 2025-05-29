```
mgradient(img; mode=:beucher, dims=coords_spatial(img), r=1)
mgradient(img, se; mode=:beucher)
```

与えられたモードを使用して画像の形態学的勾配を計算します。

広く使用されているモードは3つあります[1]:

  * `:beucher`: デフォルトモード。膨張と侵食の間の算術的差を計算します – `dilate(img, se) - erode(img, se)`。
  * `:internal`: *侵食による半勾配*とも呼ばれます。元の画像とその侵食の間の算術的差を計算します – `img - erode(img, se)`。
  * `:external`: *膨張による半勾配*とも呼ばれます。膨張と元の画像の間の算術的差を計算します – `dilate(img, se) - se`。

`se`は画像の近傍を定義する構造要素です。詳細については[`strel`](@ref)を参照してください。`se`が指定されていない場合は、フィルタリングする次元を制御するための追加のキーワード`dims`を持つ[`strel_box`](@ref)が使用され、ダイヤモンドサイズを制御するための半サイズ`r`が使用されます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(7, 7); img[3:5, 3:5] .= true; img
7×7 BitMatrix:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img)) # デフォルトモード :beucher は常に2ピクセル幅の境界を作成します
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  1  1  1  1  1  0
 0  1  1  1  1  1  0
 0  1  1  0  1  1  0
 0  1  1  1  1  1  0
 0  1  1  1  1  1  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img; mode=:internal)) # 半勾配 -- 境界は元の画像の内部にあります
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  0  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img; mode=:external)) # 半勾配 -- 境界は元の画像の外部にあります
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  1  1  1  1  1  0
 0  1  0  0  0  1  0
 0  1  0  0  0  1  0
 0  1  0  0  0  1  0
 0  1  1  1  1  1  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img, strel_diamond(img))) # ダイヤモンド形状のSEを使用
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  1  1  1  1  1  0
 0  1  1  0  1  1  0
 0  1  1  1  1  1  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
```

ビュシェオペレーターは、`mgradient(img, se; mode=:beucher) == mgradient(complement.(img), se; mode=:beucher)`という意味で自己補完的なオペレーターです。`r>1`の場合、通常は*太い勾配*と呼ばれます。線分が`se`として使用されると、勾配は*方向勾配*になります。

## 参照

  * [`mgradient!`](@ref)はこの関数のインプレースバージョンです。
  * [`mlaplacian`](@ref)はラプラスオペレーターです。
  * `ImageBase.FiniteDiff`は、`fdiff`、`fgradient`などのいくつかの有限差分オペレーターも提供します。

## 参考文献

  * [1] Rivest, Jean-Francois, Pierre Soille, and Serge Beucher. "Morphological gradients." Journal of Electronic Imaging 2.4 (1993): 326-336.
