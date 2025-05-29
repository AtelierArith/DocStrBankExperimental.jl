```
dilate(img; dims=coords_spatial(img), r=1)
dilate(img, se)
```

`img`の近傍に対して最大フィルタを実行します。近傍は構造要素`se`によって指定されます。

`se`は画像の近傍を定義する構造要素です。詳細については[`strel`](@ref)を参照してください。`se`が指定されていない場合、フィルタリングする次元を制御するために追加のキーワード`dims`を持つ[`strel_box`](@ref)が使用され、ダイヤモンドサイズを制御するために半サイズ`r`が使用されます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(5, 5); img[3, [2, 4]] .= true; img
5×5 BitMatrix:
 0  0  0  0  0
 0  0  0  0  0
 0  1  0  1  0
 0  0  0  0  0
 0  0  0  0  0

julia> dilate(img)
5×5 BitMatrix:
 0  0  0  0  0
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 0  0  0  0  0

julia> dilate(img; dims=1)
5×5 BitMatrix:
 0  0  0  0  0
 0  1  0  1  0
 0  1  0  1  0
 0  1  0  1  0
 0  0  0  0  0

julia> dilate(img, strel_diamond(img)) # ダイヤモンド形状のSEを使用
5×5 BitMatrix:
 0  0  0  0  0
 0  1  0  1  0
 1  1  1  1  1
 0  1  0  1  0
 0  0  0  0  0
```

## 参照

  * [`dilate!`](@ref)はこの関数のインプレースバージョンです
  * [`erode`](@ref)は、`complement.(dilate(img)) == erode(complement.(img))`という意味で`dilate`の双対演算子です。

!!! note "対称性"
    `se`が原点に対して対称である場合、すなわち`se[b] == se[-b]`が任意の`b`に対して成り立つ場合、膨張はミンコフスキー和になります: A⊕B={a+b|a∈A, b∈B}。

