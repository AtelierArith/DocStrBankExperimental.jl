```
ExclusiveTopology(grid::AbstractGrid)
```

The **experimental feature** `ExclusiveTopology` saves topological (connectivity/neighborhood) data of the grid. Only the highest dimensional neighborhood is saved. I.e., if something is connected by a face and an edge, only the face neighborhood is saved. The lower dimensional neighborhood is recomputed when calling getneighborhood if needed.

# Fields

  * `vertex_to_cell::AbstractArray{AbstractVector{Int}, 1}`:           global vertex id to all cells containing the vertex
  * `cell_neighbor::AbstractArray{AbstractVector{Int}, 1}`:            cellid to all connected cells
  * `face_neighbor::AbstractArray{AbstractVector{FaceIndex}, 2}`:      `face_neighbor[cellid,   local_face_id]`   -> neighboring faces
  * `edge_neighbor::AbstractArray{AbstractVector{EdgeIndex}, 2}`:      `edge_neighbor[cellid,   local_edge_id]`   -> neighboring edges
  * `vertex_neighbor::AbstractArray{AbstractVector{VertexIndex}, 2}`:  `vertex_neighbor[cellid, local_vertex_id]` -> neighboring vertices
  * `face_skeleton::Union{Vector{FaceIndex}, Nothing}`:     List of unique faces in the grid given as `FaceIndex`
  * `edge_skeleton::Union{Vector{EdgeIndex}, Nothing}`:     List of unique edges in the grid given as `EdgeIndex`
  * `vertex_skeleton::Union{Vector{VertexIndex}, Nothing}`: List of unique vertices in the grid given as `VertexIndex`

!!! warning "Limitations"
    The implementation only works with conforming grids, i.e. grids without "hanging nodes". Non-conforming grids will give unexpected results. Grids with embedded cells (different reference dimension compared to the spatial dimension) are not supported, and will error on construction.

