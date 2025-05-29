```
shape_coords(name)
```

Returns a `2 ⨯ n` `HybridMatrix` with all coordinates of the shape with the given name. Use [`shape_names`](@ref) to find all possible inputs for this function.

```julia
julia> shape_coords("Bone-1")
2×106 HybridArrays.HybridMatrix{2, StaticArraysCore.Dynamic(), Float64, 2, Matrix{Float64}} with indices SOneTo(2)×Base.OneTo(106):
 0.34174  0.3578   0.37615  0.3922   0.40826  0.42431  0.44037  0.45642  0.47248  …  0.22477  0.24083  0.25688  0.27294  0.28899  0.30505  0.32339  0.33945  0.34174
 0.5      0.52523  0.55046  0.57569  0.60092  0.62615  0.65138  0.67661  0.70183     0.31651  0.34174  0.36697  0.3922   0.41743  0.44266  0.46789  0.49312  0.5
```
