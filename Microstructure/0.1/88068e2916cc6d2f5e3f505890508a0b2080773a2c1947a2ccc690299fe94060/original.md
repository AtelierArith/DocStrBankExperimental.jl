```
Sphere(
    diff::Float64, 
    size::Float64, 
    t2::Float64
    )
```

Return a Sphere Type object with diffusivity within sphere `diff`, spherical radius `size`, and T2 relaxation time `t2`.

# Examples

```julia-repl
julia> Sphere(diff = 3.0e-9, size = 8.0e-6, t2 = 45e-3)
Sphere(3.0e-9, 8.0e-6, 0.045)
```
