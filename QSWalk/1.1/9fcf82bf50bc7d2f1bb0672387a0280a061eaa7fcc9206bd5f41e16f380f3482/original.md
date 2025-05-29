```
make_vertex_set(A[, epsilon])
```

Creates object of type `VertexSet` which represents how vertices are located in matrix. Should be used only in the nondefault use of `evolve_generator` function. It is always equal to the second element if output of `evolve_generator` function.

# Examples

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
