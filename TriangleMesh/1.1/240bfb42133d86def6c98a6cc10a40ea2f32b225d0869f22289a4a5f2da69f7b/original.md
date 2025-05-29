```
refine(m :: TriMesh ; <keyword arguments>)
```

Refines a triangular mesh according to user set constraints.

# Keyword arguments

  * `divide_cell_into :: Int = 4`: Triangles listed in `ind_cell` are area constrained                                   by 1/divide*cell*into * area(triangle[ind_cell]) in refined triangulation.
  * `ind_cell :: Array{Int,1} = collect(1:m.n_cell)`: List of triangles to be refined.
  * `keep_segments :: Bool = false`: Retain segments of input triangulations (although they may be subdivided).
  * `keep_edges :: Bool = false`: Retain edges of input triangulations (although they may be subdivided).
  * `verbose :: Bool = false`: Output triangle's commandline info.
  * `check_triangulation :: Bool = false`: Check refined mesh.
  * `voronoi :: Bool = false`: Output Voronoi diagram.
  * `output_edges :: Bool = true`: Output edges.
  * `output_cell_neighbors :: Bool = true`: Output cell neighbors.
  * `quality_meshing :: Bool = true`: No angle is is smaller than 20 degrees.
  * `info_str :: String = "Refined mesh"`: Some info string.

# Remark

The switches `keep_segments` and `keep_edges` can not be true at the same time. If `keep_segments=true` area constraints on triangles listed in `ind_cell` are rather local constraints than hard constraints on a triangle since the original edges may not be preserved. For details see Triangle's documentation. 
