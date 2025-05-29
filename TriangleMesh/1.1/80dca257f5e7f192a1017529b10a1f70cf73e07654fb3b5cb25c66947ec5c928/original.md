```
create_mesh(poly :: Polygon_pslg; <keyword arguments>)
```

Creates a triangulation of a planar straight-line graph (PSLG) polygon. 

# Keyword arguments

  * `info_str :: String = "Triangular mesh of polygon (PSLG)"`: Some mesh info on the mesh
  * `verbose :: Bool = false`: Print triangle's output
  * `check_triangulation :: Bool = false`: Check triangulation for Delaunay property                                       after it is created
  * `voronoi :: Bool = false`: Output a Voronoi diagram
  * `delaunay :: Bool = false`: If true this option ensures that the mesh is Delaunay                           instead of only constrained Delaunay. You can also set                           it true if you want to ensure that all Voronoi vertices                           are within the triangulation.
  * `mesh_convex_hull :: Bool = false`: Mesh the convex hull of a `poly` (useful if the polygon does                                       not enclose a bounded area - its convex hull still does though)
  * `output_edges :: Bool = true`: If true gives an edge list.
  * `output_cell_neighbors :: Bool = true`: If true outputs a list of neighboring triangles                                       for each triangle
  * `quality_meshing :: Bool = true`: If true avoids triangles with angles smaller that 20 degrees
  * `prevent_steiner_points_boundary :: Bool = false`: If true no Steiner points are added on                                                   boundary segnents.
  * `prevent_steiner_points :: Bool = false`: If true no Steiner points are added on boundary segments                                            on inner segments.
  * `set_max_steiner_points :: Bool = false`: If true the user will be asked to enter the maximum number                                            of Steiner points added. If the user inputs 0 this is                                            equivalent to `set_max_steiner_points = true`.
  * `set_area_max :: Bool = false`: If true the user will be asked for the maximum triangle area.
  * `set_angle_min :: Bool = false`: If true the user will be asked for a lower bound for minimum                                angles in the triangulation.
  * `add_switches :: String = ""`: The user can pass additional switches as described in triangle's                               documentation. Only set this option if you know what you are doing.
