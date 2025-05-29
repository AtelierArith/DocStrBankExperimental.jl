```
f64(m)
```

Converts the `eltype` of model's *floating point* parameters to `Float64`. Recurses into structs marked with [`@layer`](@ref Flux.@layer).

See also [`f32`](@ref) and [`f16`](@ref).
