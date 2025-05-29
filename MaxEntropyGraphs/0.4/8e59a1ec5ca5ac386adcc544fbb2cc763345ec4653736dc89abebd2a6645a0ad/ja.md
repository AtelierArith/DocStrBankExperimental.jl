```
outdegree(m::DBCM, i::Int; method=:reduced)
```

ノード `i` の DBCM モデル `m` に対する期待される次数ベクトルを返します。パフォーマンスの理由から、縮小モデルパラメータ `xᵣ` を使用します。

# 引数

  * `m::DBCM`: DBCM モデル
  * `i::Int`: 次数を計算するノード。
  * `method::Symbol`: 次数を計算するために使用するメソッド。以下のいずれかを使用できます。

      * `:reduced` (デフォルト) は、パフォーマンスの理由から縮小モデルパラメータ `xᵣ` を使用します。
      * `:full` は、期待される隣接行列のすべての要素を使用します。
      * `:adjacency` は、モデルの事前計算された隣接行列 `m.Ĝ` を使用します。

# 例

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof([outdegree(model, 1), outdegree(model, 1, method=:full), outdegree(model, 1, method=:adjacency)])
Vector{Float64} (alias for Array{Float64, 1})

```
