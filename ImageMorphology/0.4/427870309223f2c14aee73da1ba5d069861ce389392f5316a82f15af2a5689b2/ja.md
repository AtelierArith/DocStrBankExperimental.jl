```
closing(img; dims=coords_spatial(img), r=1)
closing(img, se)
```

`img`に対して形態学的クロージングを実行します。クロージング操作は、膨張の後に侵食を行うこととして定義されます：`erode(dilate(img, se), se)`。

`se`は画像の近傍を定義する構造要素です。詳細については[`strel`](@ref)を参照してください。`se`が指定されていない場合、次のキーワード`dims`を使用してフィルタリングする次元を制御し、半サイズ`r`を使用してダイヤモンドサイズを制御する[`strel_box`](@ref)が使用されます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(7,7); img[2, 2] = true; img[3:5, 3:5] .= true; img[4, 4] = false; img
7×7 BitMatrix:
 0  0  0  0  0  0  0
 0  1  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  0  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> closing(img)
7×7 BitMatrix:
 1  1  0  0  0  0  0
 1  1  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> closing(img, strel_diamond(img)) # # ダイヤモンド形状のSEを使用
7×7 BitMatrix:
 0  0  0  0  0  0  0
 0  1  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
```

## 参照

  * [`opening!`](@ref)はこの関数のインプレースバージョンです。
  * [`closing`](@ref)は、`complement.(opening(img)) == closing(complement.(img))`という意味で`opening`の双対演算子です。
