```
vtk_grid(filename,
         xs::AbstractVector,
         cells::AbstractVector{<:AbstractMeshCell};
         kwargs...)
```

Create an unstructured mesh  image data (`.vtu`) file.

`xs` is a vector of coordinates, such as a vector of `SVector{3}` elements.
