```
create_mesh(point :: Array{Float64,2}; <keyword arguments>)
```

Creates a triangulation of the convex hull of a point cloud.

# Keyword arguments

  * `point_marker :: Array{Int,2} = Array{Int,2}(undef,0,size(point,1))`: Points can have a marker.
  * `point_attribute :: Array{Float64,2} = Array{Float64,2}(undef,0,size(point,1))`: Points can be                                                                            given a number                                                                           of attributes.
  * `info_str :: String = "Triangular mesh of convex hull of point cloud."`: Some mesh info on the mesh
  * `verbose :: Bool = false`: Print triangle's output
  * `check_triangulation :: Bool = false`: Check triangulation for Delaunay property                                       after it is created
  * `voronoi :: Bool = false`: Output a Voronoi diagram
  * `delaunay :: Bool = false`: If true this option ensures that the mesh is Delaunay                           instead of only constrained Delaunay. You can also set                           it true if you want to ensure that all Voronoi vertices                           are within the triangulation.
  * `output_edges :: Bool = true`: If true gives an edge list.
  * `output_cell_neighbors :: Bool = true`: If true outputs a list of neighboring triangles                                       for each triangle
  * `quality_meshing :: Bool = true`: If true avoids triangles with angles smaller that 20 degrees
  * `prevent_steiner_points_boundary :: Bool = false`: If true no Steiner points are added on                                                   boundary segnents.
  * `prevent_steiner_points :: Bool = false`: If true no Steiner points are added on boundary segments                                            on inner segments.
  * `set_max_steiner_points :: Bool = false`: If true the user will be asked to enter the maximum number                                            of Steiner points added. If the user inputs 0 this is                                            equivalent to `set_max_steiner_points = true`.
  * `set_area_max :: Bool = false`: If true the user will be asked for the maximum triangle area.
  * `set_angle_min :: Bool = false`: If true the user will be asked for a lower bound for minimum                                angles in the triangulation.
  * `add_switches :: String = ""`: The user can pass additional switches as described in triangle's                               documentation. Only set this option if you know what you are doing.
