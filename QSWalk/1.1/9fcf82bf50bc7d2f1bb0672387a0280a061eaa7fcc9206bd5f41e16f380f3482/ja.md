```
make_vertex_set(A[, epsilon])
```

`VertexSet`型のオブジェクトを作成し、行列内の頂点の位置を表します。これは、`evolve_generator`関数の非デフォルトの使用時にのみ使用する必要があります。常に`evolve_generator`関数の出力の第二要素に等しくなります。

# 例

```jldoctest; setup = :(using QSWalk)
julia> A = [1 2 3; 0 3. 4.; 0 0 5.]
3×3 Array{Float64,2}:
 1.0  2.0  3.0
 0.0  3.0  4.0
 0.0  0.0  5.0

julia> vlist(make_vertex_set(A))
3-element Array{Vertex,1}:
 Vertex([1, 2, 3])
 Vertex([4, 5])
 Vertex([6])

julia> vlist(make_vertex_set(A, epsilon = 2.5))
3-element Array{Vertex,1}:
 Vertex([1])
 Vertex([2, 3])
 Vertex([4])
```
