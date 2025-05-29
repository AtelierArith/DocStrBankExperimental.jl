```
gpu(x, backend)
```

Tries to move `x` to the GPU backend specified in the 'backend' parameter. 

This works for functions, and any struct marked with `@functor`.

Use [`cpu`](@ref) to copy back to ordinary `Array`s.

See also [`f32`](@ref) and [`f64`](@ref) to change element type only.

# Examples

```julia
x = gpu(x, CUDABackend())
```
