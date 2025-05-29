```
str_add!(tr::Tract{T}, xyz::Vector{Matrix{Txyz}}, scalars::Union{Vector{Matrix{Ts}}, Vector{Vector{Ts}}, Nothing}=nothing, properties::Union{Matrix{Tp}, Vector{Tp}, Nothing}=nothing) where {T<:Number, Txyz<:Number, Ts<:Number, Tp<:Number}
```

Append new streamlines to a Tract structure of data type T

# Required inputs

  * tr::Tract{T}: Tract structure that the streamlines will be added to
  * xyz::Vector{Matrix}: Voxel coordinates of the points on the new streamlines [nstr][3 x npts]

# Optional inputs (required only if Tract structure contains them)

  * scalars::Union{Vector{Matrix}, Vector{Vector}, Nothing}: Scalars associated with each point on the new streamlines [nstr][nscalar x npts] or (if nscalar == 1) [nstr][npts]
  * properties::Union{Matrix, Vector, Nothing}: Properties associated with each of the new streamlines [nprop x nstr] or (if nprop == 1) [nstr]
