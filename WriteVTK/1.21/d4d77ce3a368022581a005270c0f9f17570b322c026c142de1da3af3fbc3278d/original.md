```
vtk_grid(filename,
         x::AbstractVector{T}, [y::AbstractVector{T}, [z::AbstractVector{T}]],
         cells::AbstractVector{<:AbstractMeshCell};
         kwargs...) where {T<:Number}
```

Create an unstructured mesh image data (`.vtu`) file.

`x`, `y` and `z` are vectors of containing the corresponding Cartesian coordinates of each point.
