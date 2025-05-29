```
degree(m::BiCM, i::Int; method=:reduced)
```

BiCMモデル`m`のノード`i`の期待される次数を返します。パフォーマンスの理由から、縮小モデルパラメータ`xᵣ`を使用します。

# 引数

  * `m::BiCM`: BiCMモデル
  * `i::Int`: 次数を計算するノード。このノードはモデルを定義するために使用された元のグラフのノードのいずれかであることができます。
  * `method::Symbol`: 次数を計算するために使用する方法。以下のいずれかを指定できます：

      * `:reduced`（デフォルト）は、パフォーマンスの理由から縮小モデルパラメータ`xᵣ`、`yᵣ`、`f⊥`および`f⊤`を使用します。
      * `:full`は、期待される隣接行列のすべての要素を使用します。
      * `:adjacency`は、モデルの事前計算された隣接行列`m.Ĝ`を使用します。

# 例

```jldoctest
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> typeof([degree(model, 1), degree(model, 1, method=:full), degree(model, 1, method=:adjacency)])
Vector{Float64} (alias for Array{Float64, 1})

```
