```
squares(G::Graphs.SimpleGraph)
squares(A::T; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
squares(m::UBCM)
```

無向グラフの（期待される）正方形の数を計算します。これは、隣接行列またはUBCMモデルに基づいて、グラフから直接行うことができます。

# 注意事項:

この関数では、$square$は内部に対角線のない「純粋な」正方形として理解されます。これが、三角形を含む正方形も数える誘導部分グラフのカウントとの違いを説明しています。

# 引数

隣接行列`A`には、次の引数を渡すことができます：

  * `check_dimensions`: trueの場合、`A`が正方行列であることを確認し、そうでない場合はエラーをスローします。
  * `check_directed`: trueの場合、`A`が対称であることを確認し、そうでない場合はエラーをスローします。

これらのチェックは、パフォーマンスの理由からオフにすることができます。

# 例

```jldoctest squares_doc_all
julia> G = MaxEntropyGraphs.Graphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> (squares(G), squares(MaxEntropyGraphs.Graphs.adjacency_matrix(G)), squares(model))
(36.0, 36.0, 45.644736823949344)
```
