```
grot!(geo::GenericTrace, ang::Real, axis::Vector{<:Real}, origin::Vector{<:Real}=[0])

Rotates the geometry by the specified angle `ang` around the axis `axis` and origin `origin`.

# Arguments
- `geo::GenericTrace`: The geometry to be rotated.
- `ang::Real`: The rotation angle.
- `axis::Vector{<:Real}`: The rotation axis.
- `origin::Vector{<:Real}=[0]`: The rotation origin. Defaults to the center of the geometry if not specified.
```
