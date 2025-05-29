```
vtk_grid(filename,
         X::AbstractMatrix,
         cells::AbstractVector{<:AbstractMeshCell};
         kwargs...)
```

Create an unstructured mesh  image data (`.vtu`) file.

`X` is a matrix with each column containing the Cartesian coordinates of a point
