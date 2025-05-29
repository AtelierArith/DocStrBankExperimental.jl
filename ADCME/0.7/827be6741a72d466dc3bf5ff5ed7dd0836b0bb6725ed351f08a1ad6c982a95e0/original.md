```
clip(o::Union{Array{Any}, Array{PyObject}}, vmin, vmax, args...;kwargs...)
```

Clips the values of `o` to the range [`vmin`, `vmax`]

# Example

```julia
a = constant(3.0)
a = clip(a, 1.0, 2.0)
b = constant(rand(3))
b = clip(b, 0.5, 1.0)
```
