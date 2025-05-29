```
outdegree(m::DBCM[, v]; method=:reduced)
```

DBCMモデル`m`の各ノードの期待される出次数に対応するベクトルを返します。vが指定されている場合、vのノードの出次数のみを返します。

# 引数

  * `m::DBCM`: DBCMモデル
  * `v::Vector{Int}`: 出次数を計算するノード。デフォルトはすべてのノード。
  * `method::Symbol`: 出次数を計算するために使用する方法。以下のいずれかを指定できます。

      * `:reduced`（デフォルト）は、パフォーマンスの理由から縮小モデルパラメータ`xᵣ`を使用します。
      * `:full`は、期待される隣接行列のすべての要素を使用します。
      * `:adjacency`は、モデルの事前計算された隣接行列`m.Ĝ`を使用します。

# 例

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof(outdegree(model, method=:adjacency)) 
Vector{Float64} (alias for Array{Float64, 1})

```
