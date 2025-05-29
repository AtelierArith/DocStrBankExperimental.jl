```
ellipsoids(origin::Vector{<:Real}, par::Vector{<:Real}, color::String=""; opc::Real=1, tres=61, pres=31, ah::Real=0)

Creates a 3D ellipsoid mesh.

# Arguments
- `origin::Vector{<:Real}`: The center of the ellipsoid.
- `par::Vector{<:Real}`: Parameters of the ellipsoid (a, b, c).
- `color::String`: The color of the ellipsoid.

# Keywords
- `opc`: The opacity of the ellipsoid. Default is 1.
- `tres`: The resolution of the mesh grid (theta). Default is 61.
- `pres`: The resolution of the mesh grid (phi). Default is 31.
- `ah`: alphahull value. Default is 0.
```
