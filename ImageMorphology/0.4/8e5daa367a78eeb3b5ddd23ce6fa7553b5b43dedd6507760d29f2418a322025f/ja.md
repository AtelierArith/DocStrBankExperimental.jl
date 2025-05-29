```
label = label_components(A; [dims=coords_spatial(A)], [r=1], [bkg])
label = label_components(A, se; [bkg])

配列 `A` の接続成分を見つけてラベル付けします。接続性は構造要素 `se` によって定義されます。各成分には一意の整数値がラベルとして割り当てられ、`0` は `bkg` で定義された背景を表します。

`se` は画像の近傍を定義する構造要素です。詳細については [`strel`](@ref) を参照してください。`se` が指定されていない場合は、次のキーワード `dims` を使用してフィルタリングする次元を制御し、半サイズ `r` を使用してダイヤモンドサイズを制御する [`strel_box`](@ref) が使用されます。

# 例

```

jldoctest; setup=:(using ImageMorphology) julia> A = [false true false true  false;             true false false  true  true] 2×5 Matrix{Bool}:  0  1  0  1  0  1  0  0  1  1

julia> label_components(A) # デフォルトのダイヤモンド形状 C4 接続性 2×5 Matrix{Int64}:  0  2  0  3  0  1  0  0  3  3

julia> label_components(A; dims=2) # 行のみが考慮される 2×5 Matrix{Int64}:  0  2  0  3  0  1  0  0  4  4

julia> label*components(A, strel*box((3, 3))) # ボックス形状 C8 接続性 2×5 Matrix{Int64}:  0  1  0  2  0  1  0  0  2  2

```

インプレースバージョンは [`label_components!`](@ref) です。ラベル付けされた成分の基本的な特性については、[`component_boxes`](@ref)、[`component_lengths`](@ref)、[`component_indices`](@ref)、[`component_centroids`](@ref) も参照してください。
```
