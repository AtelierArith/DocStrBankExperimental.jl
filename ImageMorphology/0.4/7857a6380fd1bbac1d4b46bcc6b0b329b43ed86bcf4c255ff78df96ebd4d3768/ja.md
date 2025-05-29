```
tophat(img; dims=coords_spatial(img), r=1)
tophat(img, se)
```

与えられた画像に対して形態学的トップハット変換を実行します。すなわち、`img - opening(img, se)`です。

`se`は画像の近傍を定義する構造要素です。詳細については[`strel`](@ref)を参照してください。`se`が指定されていない場合、次のキーワード`dims`を使用してフィルタリングする次元を制御し、半サイズ`r`を使用してダイヤモンドサイズを制御する[`strel_box`](@ref)が使用されます。

この*白*トップハット変換は、画像から小さな白い要素や詳細を抽出するために使用できます。黒い詳細を抽出するには、*黒*トップハット変換、別名ボトムハット変換、[`bothat`](@ref)を使用できます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(5, 5); img[1, 1] = true; img[3:5, 3:5] .= true; img
5×5 BitMatrix:
 1  0  0  0  0
 0  0  0  0  0
 0  0  1  1  1
 0  0  1  1  1
 0  0  1  1  1

julia> Int.(tophat(img))
5×5 Matrix{Int64}:
 1  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0

julia> Int.(tophat(img, strel_diamond(img))) # ダイヤモンド形状のSEを使用
5×5 Matrix{Int64}:
 1  0  0  0  0
 0  0  0  0  0
 0  0  1  0  0
 0  0  0  0  0
 0  0  0  0  0
```
