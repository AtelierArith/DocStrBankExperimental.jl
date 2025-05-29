```
out = erode(img; dims=coords_spatial(img), r=1)
out = erode(img, se)
```

`img`の近傍に対して最小フィルタを実行します。近傍は構造要素`se`によって指定されます。

`se`は画像の近傍を定義する構造要素です。詳細については[`strel`](@ref)を参照してください。`se`が指定されていない場合、フィルタリングする次元を制御するための追加のキーワード`dims`を持つ[`strel_box`](@ref)が使用され、ダイヤモンドサイズを制御するための半サイズ`r`が使用されます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = trues(5, 5); img[3, [2, 4]] .= false; img
5×5 BitMatrix:
 1  1  1  1  1
 1  1  1  1  1
 1  0  1  0  1
 1  1  1  1  1
 1  1  1  1  1

julia> erode(img)
5×5 BitMatrix:
 1  1  1  1  1
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 1  1  1  1  1

julia> erode(img; dims=1)
5×5 BitMatrix:
 1  1  1  1  1
 1  0  1  0  1
 1  0  1  0  1
 1  0  1  0  1
 1  1  1  1  1

julia> erode(img, strel_diamond(img)) # ダイヤモンド形状のSEを使用
5×5 BitMatrix:
 1  1  1  1  1
 1  0  1  0  1
 0  0  0  0  0
 1  0  1  0  1
 1  1  1  1  1
```

## 参照

  * [`erode!`](@ref)はこの関数のインプレースバージョンです
  * [`dilate`](@ref)は、`complement.(dilate(img)) == erode(complement.(img))`という意味で`erode`の双対演算子です。

!!! note "対称性"
    `se`が原点に関して対称である場合、すなわち、任意の`b`に対して`se[b] == se[-b]`である場合、侵食はミンコフスキー差になります：A⊖B={a-b|a∈A, b∈B}。

