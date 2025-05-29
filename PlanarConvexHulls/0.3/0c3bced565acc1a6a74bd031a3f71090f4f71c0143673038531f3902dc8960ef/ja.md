```julia
is_ordered_and_strongly_convex(vertices, order)

```

`vertices`が頂点順序タイプ`O`（[`VertexOrder`](@ref)のサブタイプ）に従って順序付けられているかどうかを返し、その結果*強い*凸であるかどうかを返します（強い凸性の定義については、例えば[CGALのドキュメント](https://doc.cgal.org/latest/Convex_hull_2/index.html)を参照してください）。
