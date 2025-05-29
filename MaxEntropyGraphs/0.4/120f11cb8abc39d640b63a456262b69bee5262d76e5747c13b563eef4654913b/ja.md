```
degree(m::UBCM, i::Int; method=:reduced)
```

ノード `i` の UBCM モデル `m` の期待される次数を返します。パフォーマンスの理由から、縮小モデルパラメータ `xᵣ` を使用します。

# 引数

  * `m::UBCM`: UBCM モデル
  * `i::Int`: 次数を計算するノード。
  * `method::Symbol`: 次数を計算するために使用するメソッド。以下のいずれかを使用できます。

      * `:reduced` (デフォルト) は、パフォーマンスの理由から縮小モデルパラメータ `xᵣ` を使用します。
      * `:full` は、期待される隣接行列のすべての要素を使用します。
      * `:adjacency` は、モデルの事前計算された隣接行列 `m.Ĝ` を使用します。

# 例

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof([degree(model, 1), degree(model, 1, method=:full), degree(model, 1, method=:adjacency)])
Vector{Float64} (alias for Array{Float64, 1})

```
