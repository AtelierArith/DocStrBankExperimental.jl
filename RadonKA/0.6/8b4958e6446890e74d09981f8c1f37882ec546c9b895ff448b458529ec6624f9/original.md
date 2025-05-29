```
radon(I, θs; <kwargs>)
```

Calculates the parallel Radon transform of the AbstractArray `I`. Intuitively, the `radon` sums array entries  of `I` along ray paths.

The first two dimensions are y and x. The third dimension is z, the rotational axis. `size(I, 1)` and `size(I, 2)` have to be equal. The Radon transform is rotated around the pixel `size(I, 1) ÷ 2 + 1`, so there is always an integer center pixel! Works either with a `AbstractArray{T, 3}` or `AbstractArray{T, 2}`.

`θs` is a vector or range storing the angles in radians.

In principle, all backends of KernelAbstractions.jl should work but are not tested. CUDA and CPU arrays are actively tested. Both `radon` and [`backproject`](@ref) are differentiable with respect to `I`.

# Keywords

## `μ=nothing` - Attenuated Radon Transform

If `μ != nothing`, then the rays are attenuated with `exp(-μ * dist)` where `dist`  is the distance to the circular boundary of the field of view. `μ` is in units of pixel length. So `μ=1` corresponds to an attenuation of `exp(-1)` if propagated through one pixel. If `isnothing(μ)`, then the rays are not attenuated.

`μ` can be also an array of the same size as `I` which allows for spatially varying attenuation. For example, `μ=0.01`  and `μ = ones(size(I)) * 0.01` are equivalent. In practice there is a slight difference because we calculate the attenuation differently.

## `geometry = RadonParallelCircle(-(size(img,1)-1)÷2:(size(img,1)-1)÷2)`

This corresponds to a parallel Radon transform.  See `?RadonGeometries` for a full list of geometries. There is also the very flexible `RadonFlexibleCircle`.

See also [`backproject`](@ref).

# Example

The reason the sinogram has the value `1.41421` for the diagonal ray `π/4` is, that such a diagonal travels a longer distance through the pixel.

```jldoctest
julia> arr = zeros((4,4)); arr[3,3] = 1;

julia> radon(arr, [0, π/4, π/2])
3×3 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0      0.0
 1.0  1.41421  1.0
 0.0  0.0      0.0
```

## Choose different detector

```jldoctest
julia> array = ones((6,6))
6×6 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0

julia> radon(array, [0])
5×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 1.0
 3.7320508075688767
 5.0
 3.7320508075688767
 1.0

julia> radon(array, [0], geometry=RadonParallelCircle(6, -2:2))
5×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 1.0
 3.7320508075688767
 5.0
 3.7320508075688767
 1.0

julia> radon(array, [0], geometry=RadonParallelCircle(6, -2:2:2))
3×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 1.0
 5.0
 1.0
```

## Apply some weights on the rays

```jldoctest
julia> array = ones((6,6));

julia> radon(array, [0], geometry=RadonParallelCircle(6, -2:2, [2,1,0,1,2]))
5×1 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 2.0
 3.7320508075688767
 0.0
 3.7320508075688767
 2.0
```
