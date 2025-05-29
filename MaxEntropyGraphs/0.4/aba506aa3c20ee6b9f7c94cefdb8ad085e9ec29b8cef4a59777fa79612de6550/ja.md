```
wedges(G::Graphs.SimpleGraph)
wedges(A::T; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
wedges(m::UBCM)
```

無向グラフの（期待される）ウェッジの数を計算します。グラフから直接、隣接行列に基づいて、またはUBCMモデルを使用して行うことができます。

# 引数

隣接行列 `A` に対して、次の引数を渡すことができます：

  * `check_dimensions`: trueの場合、`A` が正方行列であることを確認し、そうでない場合はエラーをスローします。
  * `check_directed`: trueの場合、`A` が対称であることを確認し、そうでない場合はエラーをスローします。

# 例

```jldoctest wedges_graph_docs
julia> G = MaxEntropyGraphs.Graphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> (wedges(G), wedges(MaxEntropyGraphs.Graphs.adjacency_matrix(G)), wedges(model))
(528.0, 528.0, 528.0000011499742)
```
