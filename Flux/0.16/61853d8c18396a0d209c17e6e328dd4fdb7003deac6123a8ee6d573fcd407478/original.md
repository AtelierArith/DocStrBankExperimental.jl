```
gpu(m)
```

Copies `m` to the current GPU device (using current GPU backend), if one is available. If no GPU is available, it does nothing (but prints a warning the first time). It recurses into structs according to Functors.jl.

Use [`cpu`](@ref) to copy back to ordinary `Array`s. See also [`f32`](@ref) and [`f16`](@ref) to change element type only.

This function is just defined for convenience around [`gpu_device`](@ref),  and is equivalent to `gpu_device()(m)`. You may consider defining `device = gpu_device()` once and then using `device(m)` to move data.

# Example

```julia-repl
julia> m = Dense(rand(2, 3))  # constructed with Float64 weight matrix
Dense(3 => 2)       # 8 parameters

julia> typeof(m.weight)
Matrix{Float64} (alias for Array{Float64, 2})

julia> m_gpu = gpu(m)  # can equivalently be written m_gpu = m |> gpu
Dense(3 => 2)       # 8 parameters

julia> typeof(m_gpu.weight)
CUDA.CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}
```
