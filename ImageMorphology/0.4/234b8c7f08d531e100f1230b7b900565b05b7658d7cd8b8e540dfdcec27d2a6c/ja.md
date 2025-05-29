```
bothat(img; dims=coords_spatial(img), r=1)
bothat(img, se)
```

与えられた画像に対して形態学的ボトムハット変換を実行します。すなわち、`closing(img, se) - img`です。

`se`は画像の近傍を定義する構造要素です。詳細については[`strel`](@ref)を参照してください。`se`が指定されていない場合、次のキーワード`dims`を使用してフィルタリングする次元を制御し、半サイズ`r`を使用してダイヤモンドサイズを制御する[`strel_box`](@ref)が使用されます。

このボトムハット変換は、*黒*トップハット変換とも呼ばれ、画像から小さな黒い要素や詳細を抽出するために使用できます。白い詳細を抽出するには、*白*トップハット変換[`tophat`](@ref)を使用できます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(7, 7); img[3:5, 3:5] .= true; img[4, 6] = true; img[4, 4] = false; img
7×7 BitMatrix:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  0  1  1  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(bothat(img))
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  1  0  0  1
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(bothat(img, strel_diamond(img))) # ダイヤモンド形状のSEを使用
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  1  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
```

インプレースバージョンについては、[`bothat!`](@ref)も参照してください。
