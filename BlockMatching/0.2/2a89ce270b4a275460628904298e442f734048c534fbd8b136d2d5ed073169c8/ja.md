```
best_match(S::AbstractBlockMatchingStrategy, ref, [frame=ref]; offset=false)
best_match(S::AbstractBlockMatchingStrategy, ref, [frame=ref], p; offset=false)
```

与えられた画素 `p` が `frame` にある場合、ブロックマッチング戦略 `S` を用いて参照画像 `ref` の中で最も適合する画素 `q` を見つけます。`p` が提供されていない場合、すべての画素 `p ∈ CartesianIndices(ref)` に対して動作し、配列を返します。

!!! note
    明確にするために、ここでの「画素」とは値 `Colorant` ではなく位置 `CartesianIndex` を意味します。


# 引数

  * `S::AbstractBlockMatchingStrategy`: 必須 具体的なブロックマッチング戦略と関連する設定（例：パッチサイズ、探索ウィンドウサイズ）。可能な戦略については `subtypes(BlockMatching.AbstractBlockMatchingStrategy)` を参照してください。
  * `ref`::AbstractArray: 必須 マッチした画素 `q` が属する参照画像。
  * `frame::AbstractArray`: オプション 現在の画像/フレームで、入力画素 `p` が属するもの。`frame` が提供されていない場合、`ref` になります。
  * `p::CartesianIndex`: オプション ブロックマッチングが動作する指定された画素 `p`。提供されない場合、ブロックマッチングは全画像に対して動作し、画素 `q` の配列を返します。

# パラメータ

  * `offset::Bool`: オプション `true` の場合、画素 `q` の代わりに動きベクトル `q-p` を返します。デフォルト値は `false` です。

# 出力

`p` が与えられた場合、`CartesianIndex{N}` を返します。そうでない場合、ブロックマッチングは全画像に対して動作し、`Array{CartesianIndex{N}, N}`、すなわち動き場を返します。

# 例

画素 `p` が提供されると、ブロックマッチングは指定された画素のみに対して動作し、出力は `p` に対するマッチした画素 `q` になります。

```jldoctest best_match
using Images, TestImages
using BlockMatching

ref = imresize(testimage("cameraman"), (64, 64))
img = imrotate(ref, 0.2, CartesianIndices(ref).indices)

S = FullSearch(SqEuclidean(), ndims(img), patch_radius=5, search_radius=11)
p = CartesianIndex(17, 17)
best_match(S, img, ref, p)

# 出力

CartesianIndex(17, 14)
```

`p` が提供されていない場合、ブロックマッチングは全画像に対して動作します。出力配列の各項目は `p` に対するマッチした画素 `q` であり、すなわち `best_match(S, ref, frame)[p] = best_match(S, ref, frame, p)` です。

```jldoctest best_match
julia> matches = best_match(S, img, ref);

julia> summary(matches)
"64×64 Matrix{CartesianIndex{2}}"

julia> matches[p] == best_match(S, img, ref, p)
true
```

!!! tip
    `best_match(S, ref, frame)` は通常 `map(p->best_match(S, ref, frame, p), CartesianIndices(frame))` よりもパフォーマンスが良いです。なぜなら、中間結果をキャッシュ/事前割り当てすることで、不必要な計算とメモリ割り当てを減らすことができるからです。


# 参照

  * [`multi_match`](@ref) は複数の候補が必要な場合に使用できます。

```
