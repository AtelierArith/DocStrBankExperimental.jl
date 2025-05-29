```
orient_normals!(search_method::KNearestSearch, normals::AbstractVector{<:AbstractVector}, points)
```

Correct the orientation of normals on a surface as the [compute_normals](@ref) function does not guarantee if the normal is inward or outward facing. Uses the approach from "Surface Reconstruction from Unorganized Points" - Hoppe (1992).
