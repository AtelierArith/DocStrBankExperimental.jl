```
imrotate(arr::AbstractArray{T, 4}, θ; method=:bilinear, rotation_center=size(arr) .÷ 2 .+ 1)
```

Rotates an array in the first two dimensions around the center pixel `rotation_center`.  The default value of `rotation_center` is defined such that there is a integer center pixel for even and odd sized arrays which it is rotated around. For an even sized array of size `(4,4)` this would be `(3,3)`, for an odd array of size `(3,3)` this would be `(2,2)` However, `rotation_center` can be also non-integer numbers if specified.

The angle `θ` is interpreted in radians.

The adjoint is defined with ChainRulesCore.jl. This method also runs with CUDA (and in principle all KernelAbstractions.jl supported backends).

# Keywords

  * `method=:bilinear` for bilinear interpolation or `method=:nearest` for nearest neighbour
  * `rotation_center=size(arr) .÷ 2 .+ 1` means there is a real center pixel around it is rotated.

# Examples

```julia-repl
julia> arr = zeros((4,4,1,1)); arr[2,2,1,1] = 1;

julia> arr
4×4×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> NNlib.imrotate(arr, deg2rad(90)) # rotation around (3,3)
4×4×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> NNlib.imrotate(arr, deg2rad(90), rotation_center=(2,2))
4×4×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> arr = zeros((3,3,1,1)); arr[1,2,1,1] = 1
1

julia> arr
3×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  1.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> NNlib.imrotate(arr, deg2rad(45))
3×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.207107  0.0
 0.0  0.0       0.207107
 0.0  0.0       0.0

julia> NNlib.imrotate(arr, deg2rad(45), method=:nearest)
3×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  0.0  1.0
 0.0  0.0  0.0
 0.0  0.0  0.0
```
