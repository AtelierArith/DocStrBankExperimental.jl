```
multi_match(S::AbstractBlockMatchingStrategy, ref, [frame=ref]; num_patches, offset=true)
multi_match(S::AbstractBlockMatchingStrategy, ref, [frame=ref], p::CartesianIndex; num_patches, offset=true)
```

与えられた画素 `p` が `frame` にある場合、ブロックマッチング戦略 `S` を用いて `ref` 内の一致した画素 `q` を見つけます。

# 引数

  * `S::AbstractBlockMatchingStrategy`: 必須 コンクリートなブロックマッチング戦略と関連する設定、例えば、類似度測定、パッチサイズ、探索ウィンドウサイズ。可能な戦略については `subtypes(BlockMatching.AbstractBlockMatchingStrategy)` を参照してください。
  * `ref`::AbstractArray: 必須 一致した画素 `q` が属する参照画像。
  * `frame::AbstractArray`: オプション 入力画素 `p` が属する現在の画像/フレーム。`frame` が提供されない場合、`ref` が使用されます。
  * `p::CartesianIndex`: オプション ブロックマッチングが操作する与えられた画素 `p`。提供されない場合、ブロックマッチングは全画像に対して操作し、画素 `q` の配列を返します。

# パラメータ

  * `num_patches`: 必須 一致した画素の数。候補の数が `num_patches` より少ない場合、動作は未定義であり、エラーをスローする可能性があります。
  * `offset::Bool`: オプション `true` の場合、画素 `q` の代わりに動きベクトル `q-p` を返します。デフォルト値は `false` です。

# 出力

`p` が与えられた場合、`Vector{CartesianIndex{N}}` を返します。そうでない場合、ブロックマッチングは全画像に対して操作し、マッチしたベクトルを格納する追加の N+1 次元を持つ `Array{CartesianIndex{N}, N+1}` を返します。

# 例

画素 `p` が提供されると、ブロックマッチングは与えられた画素のみに操作し、出力は `p` に対する一致した画素 `q` です。

```jldoctest multi_match
using Images, TestImages
using BlockMatching

ref = imresize(testimage("cameraman"), (64, 64))
img = imrotate(ref, 0.2, CartesianIndices(ref).indices)

S = FullSearch(SqEuclidean(), ndims(img), patch_radius=5, search_radius=11)
p = CartesianIndex(17, 17)
multi_match(S, img, ref, p; num_patches=2)

# 出力

2-element Vector{CartesianIndex{2}}:
 CartesianIndex(17, 14)
 CartesianIndex(18, 13)
```

そうでない場合、ブロックマッチングは全画像に対して操作します。出力配列の各項目は `p` に対する一致した画素 `q` であり、すなわち `multi_match(S, ref, frame)[p] = multi_match(S, ref, frame, p)` です。

```jldoctest multi_match
julia> matches = multi_match(S, img, ref; num_patches=2);

julia> summary(matches)
"64×64 Matrix{Vector{CartesianIndex{2}}}"

julia> matches[p, :] == multi_match(S, img, ref, p; num_patches=2)
true
```

!!! tip
    `multi_match(S, ref, frame)` は通常 `map(p->multi_match(S, ref, frame, p), CartesianIndices(frame))` よりもパフォーマンスが良いです。なぜなら、中間結果をキャッシュすることで計算とメモリ割り当てを削減できるからです。


# 参照

[`best_match`](@ref) は `num_patches==1` の場合によりパフォーマンスが良い選択です。また、ThreeStepSearch のようなより洗練された戦略もサポートしています。
