```
orient_normals!(normals::Vector{<:AbstractVector}, points; k::Int=5)
```

Correct the orientation of normals on a surface as the [compute_normals](@ref) function does not guarantee if the normal is inward or outward facing. Uses the approach from "Surface Reconstruction from Unorganized Points" - Hoppe (1992).
