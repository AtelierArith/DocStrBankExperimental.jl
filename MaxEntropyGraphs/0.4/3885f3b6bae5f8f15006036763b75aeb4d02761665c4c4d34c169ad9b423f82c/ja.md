```
triangles(G::Graphs.SimpleGraph)
triangles(A::T; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
triangles(m::UBCM)
```

無向グラフの（期待される）三角形の数を計算します。グラフから直接、隣接行列またはUBCMモデルに基づいて行うことができます。

# 引数

隣接行列 `A` に対して、以下の引数を渡すことができます：

  * `check_dimensions`: trueの場合、`A` が正方行列であることを確認し、そうでない場合はエラーをスローします。
  * `check_directed`: trueの場合、`A` が対称であることを確認し、そうでない場合はエラーをスローします。

これらのチェックは、パフォーマンスの理由からオフにすることができます。

# 例

```jldoctest triangles_doc_all
julia> G = MaxEntropyGraphs.Graphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> (triangles(G), triangles(MaxEntropyGraphs.Graphs.adjacency_matrix(G)), triangles(model))
(45, 45.0, 52.849301363026846)
```
