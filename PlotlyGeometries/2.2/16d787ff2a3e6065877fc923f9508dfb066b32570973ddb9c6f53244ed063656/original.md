```
spheres(origin::Vector{<:Real}, r::Real, color::String=""; opc::Real=1, tres=60, pres=30, ah::Real=0)

Creates a 3D sphere mesh.

# Arguments
- `origin::Vector{<:Real}`: The center of the ellipsoid.
- `r::Real`: Radius of the sphere.
- `color::String`: The color of the ellipsoid.

# Keywords
- `opc`: The opacity of the ellipsoid. Default is 1.
- `tres`: The resolution of the mesh grid (theta). Default is 60.
- `pres`: The resolution of the mesh grid (phi). Default is 30.
- `ah`: alphahull value. Default is 0.
```
