```
gpu(x)
```

Moves 'x' to the GPU. For this function to work, a GPU backend will need to be loaded with 'using AMDGPU / CUDA / Metal / oneAPI.

This works for functions, and any struct marked with `@functor`.

Use [`cpu`](@ref) to copy back to ordinary `Array`s.

See also [`f32`](@ref) and [`f64`](@ref) to change element type only.

# Examples

```julia
using CUDA
x = x |> gpu
```
