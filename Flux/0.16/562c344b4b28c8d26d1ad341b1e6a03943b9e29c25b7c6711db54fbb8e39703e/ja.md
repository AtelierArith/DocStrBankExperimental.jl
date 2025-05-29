```
Embedding(in => out; init=randn32)
```

語彙サイズ `in` の次元 `out` の埋め込みを格納するルックアップテーブルで、学習可能な行列です。

このレイヤーは、単語の埋め込みを格納し、インデックスを使用してそれらを取得するためによく使用されます。レイヤーへの入力は、`1:in` の語彙インデックス、インデックスの配列、または対応する [`onehot encoding`](@ref OneHotArrays.onehotbatch) であることができます。

インデックス `x` に対して、結果のサイズは `(out, size(x)...)` であり、複数のバッチ次元を許可します。ワンホット `ohx` に対して、結果のサイズは `(out, size(ohx)[2:end]...)` です。

# 例

```jldoctest
julia> emb = Embedding(26 => 4, init=Flux.identity_init(gain=22))
Embedding(26 => 4)  # 104 パラメータ

julia> emb(2)  # e.weight の1列 (ここではランダムではない!)
4-element Vector{Float32}:
  0.0
 22.0
  0.0
  0.0

julia> emb([3, 1, 20, 14, 4, 15, 7])  # 語彙インデックス, in 1:26
4×7 Matrix{Float32}:
  0.0  22.0  0.0  0.0   0.0  0.0  0.0
  0.0   0.0  0.0  0.0   0.0  0.0  0.0
 22.0   0.0  0.0  0.0   0.0  0.0  0.0
  0.0   0.0  0.0  0.0  22.0  0.0  0.0

julia> ans == emb(Flux.onehotbatch("cat&dog", 'a':'z', 'n'))
true

julia> emb(rand(1:26, (10, 1, 12))) |> size  # 3つのバッチ次元
(4, 10, 1, 12)
```
