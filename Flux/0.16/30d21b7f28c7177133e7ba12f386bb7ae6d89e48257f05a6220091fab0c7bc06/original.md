```
f32(m)
```

Converts the `eltype` of model's *floating point* parameters to `Float32` (which is Flux's default). Recurses into structs marked with [`@layer`](@ref Flux.@layer).

See also [`f64`](@ref) and [`f16`](@ref).
