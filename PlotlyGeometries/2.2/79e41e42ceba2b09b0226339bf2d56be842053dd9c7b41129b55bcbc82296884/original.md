```
polygons(pts::Vector, ng::Int, color::String; opc::Real=1, ah::Real=0)

Creates a group of polygons from a set of points and a specified number of vertices per polygon.

# Arguments
- `pts::Vector`: List of points defining the mesh.
- `ng::Int`: Number of vertices per polygon.
- `color::String`: The color of the mesh.

# Keywords
- `opc`: The opacity of the mesh. Default is 1.
- `ah`: alphahull value.
```
