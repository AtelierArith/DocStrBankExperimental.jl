```
refine(m :: TriMesh, switches :: String; <keyword arguments>)
```

Refines a triangular mesh according to user set constraints. Command line switches are passed directly. Use this function only if you know what you are doing.

# Keyword arguments

  * `divide_cell_into :: Int = 4`: Triangles listed in `ind_cell` are area constrained                                   by 1/divide*cell*into * area(triangle[ind_cell]) in refined triangulation.
  * `ind_cell :: Array{Int,1} = collect(1:m.n_cell)`: List of triangles to be refined.
  * `info_str :: String = "Refined mesh"`: Some info string.
