```
degree(m::DBCM, i::Int; method=:reduced)
```

`Graphs.jl`に従い、DBCMモデル`m`のノード`i`の期待される出次数と入次数の合計を返します。パフォーマンスの理由から、縮小モデルパラメータ`xᵣ`を使用します。

# 引数

  * `m::DBCM`: DBCMモデル
  * `i::Int`: 次数を計算するノード。
  * `method::Symbol`: 次数を計算するために使用するメソッド。以下のいずれかを指定できます。

      * `:reduced`（デフォルト）は、パフォーマンスの理由から縮小モデルパラメータ`xᵣ`を使用します。
      * `:full`は、期待される隣接行列のすべての要素を使用します。
      * `:adjacency`は、モデルの事前計算された隣接行列`m.Ĝ`を使用します。

# 例

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof([degree(model, 1), degree(model, 1, method=:full), degree(model, 1, method=:adjacency)])
Vector{Float64} (alias for Array{Float64, 1})

```
