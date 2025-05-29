```
GridGraph{
    R<:Real,
    W<:AbstractMatrix{R},
    A<:AbstractMatrix{Bool},
    D<:NTuple{<:Any,GridDirection}
}
```

Graph defined by a rectangular grid of vertices.

# Fields

  * `vertex_weights::W`: Vertex weight matrix used to define edge weights.
  * `vertex_activities::A`: Vertex activity matrix. All the vertices on the grid exist, but only active vertices can have edges (inactive vertices are isolated, they correspond to obstacles).
  * `directions::D`: Set of legal directions used to define edges.
  * `nb_corners_for_diag::Int`: Number of active corner vertices necessary for a diagonal edge to exist. Can take the values `0`, `1` or `2`.
  * `pythagoras_cost_for_diag::Bool`: Whether the weight of a diagonal edge is computed using the shortest of the active corner paths (`true`) or just the weight of the arrival vertex (`false`).

# Constructors

There is a user-friendly constructor with the following default values:

```
GridGraph(
    vertex_weights;
    vertex_activities=Trues(size(weights)),
    directions=ROOK_DIRECTIONS,
    nb_corners_for_diag=0,
    pythagoras_cost_for_diag=false
)
```
