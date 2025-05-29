```
opening(img; dims=coords_spatial(img), r=1)
opening(img, se)
```

`img`に対して形態学的オープニングを実行します。オープニング操作は、侵食の後に膨張を行うこととして定義されます：`dilate(erode(img, se), se)`。

`se`は画像の近傍を定義する構造要素です。詳細については[`strel`](@ref)を参照してください。`se`が指定されていない場合、次のキーワード`dims`を使用してフィルタリングする次元を制御し、半サイズ`r`を使用してダイヤモンドサイズを制御する[`strel_box`](@ref)が使用されます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = trues(7,7); img[2, 2] = false; img[3:5, 3:5] .= false; img[4, 4] = true; img
7×7 BitMatrix:
 1  1  1  1  1  1  1
 1  0  1  1  1  1  1
 1  1  0  0  0  1  1
 1  1  0  1  0  1  1
 1  1  0  0  0  1  1
 1  1  1  1  1  1  1
 1  1  1  1  1  1  1

julia> opening(img)
7×7 BitMatrix:
 0  0  1  1  1  1  1
 0  0  1  1  1  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  1  1  1  1  1
 1  1  1  1  1  1  1

julia> opening(img, strel_diamond(img)) # ダイヤモンド形状のSEを使用
7×7 BitMatrix:
 1  1  1  1  1  1  1
 1  0  1  1  1  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  1  1  1  1  1
 1  1  1  1  1  1  1
```

## 参照

  * [`opening!`](@ref)はこの関数のインプレースバージョンです。
  * [`closing`](@ref)は、`complement.(opening(img)) == closing(complement.(img))`という意味で`opening`の双対演算子です。
