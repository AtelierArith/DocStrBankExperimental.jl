```
create_mesh(point :: Array{Float64,2}, switches :: String; <keyword arguments>)
```

Creates a triangulation of a planar straight-line graph (PSLG) polygon.  Options for the meshing algorithm are passed directly by command line switches for Triangle. Use only if you know what you are doing.

# Keyword arguments

  * `point_marker :: Array{Int,2} = Array{Int,2}(undef,0,size(point,1))`: Points can have a marker.
  * `point_attribute :: Array{Float64,2} = Array{Float64,2}(undef,0,size(point,1))`: Points can be                                                                            given a number                                                                           of attributes.
  * `info_str :: String = "Triangular mesh of convex hull of point cloud."`: Some mesh info on the mesh
