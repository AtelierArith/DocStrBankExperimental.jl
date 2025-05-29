```
cu(A; unified=false)
```

Opinionated GPU array adaptor, which may alter the element type `T` of arrays:

  * For `T<:AbstractFloat`, it makes a `CuArray{Float32}` for performance reasons. (Except that `Float16` and `BFloat16` element types are not changed.)
  * For `T<:Complex{<:AbstractFloat}` it makes a `CuArray{ComplexF32}`.
  * For other `isbitstype(T)`, it makes a `CuArray{T}`.

By contrast, `CuArray(A)` never changes the element type.

Uses Adapt.jl to act inside some wrapper structs.

# Examples

```
julia> cu(ones(3)')
1×3 adjoint(::CuArray{Float32, 1, CUDA.DeviceMemory}) with eltype Float32:
 1.0  1.0  1.0

julia> cu(zeros(1, 3); unified=true)
1×3 CuArray{Float32, 2, CUDA.UnifiedMemory}:
 0.0  0.0  0.0

julia> cu(1:3)
1:3

julia> CuArray(ones(3)')  # ignores Adjoint, preserves Float64
1×3 CuArray{Float64, 2, CUDA.DeviceMemory}:
 1.0  1.0  1.0

julia> adapt(CuArray, ones(3)')  # this restores Adjoint wrapper
1×3 adjoint(::CuArray{Float64, 1, CUDA.DeviceMemory}) with eltype Float64:
 1.0  1.0  1.0

julia> CuArray(1:3)
3-element CuArray{Int64, 1, CUDA.DeviceMemory}:
 1
 2
 3
```
