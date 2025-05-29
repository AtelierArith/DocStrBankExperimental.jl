```
set_model_geometry(reaction, model)
```

Optional: define [`Domain`](@ref) `grid`, `data_dims`.

One Reaction per Domain may create a grid (an [`AbstractMesh`](@ref) subtype) and set the `domain.grid` field.

Multiple Reactions per domain may call [`set_data_dimension!`](@ref) to define (different) named data dimensions (eg wavelength grids).
