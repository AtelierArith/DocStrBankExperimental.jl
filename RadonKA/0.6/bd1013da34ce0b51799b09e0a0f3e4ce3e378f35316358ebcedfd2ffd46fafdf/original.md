```
backproject(sinogram, θs; <kwargs>)
```

Conceptually the adjoint operation of [`radon`](@ref). Intuitively, the `backproject` smears rays back into the space. See also [`radon`](@ref).

For filtered backprojection see [`backproject_filtered`](@ref).

# Example

```jldoctest
julia> arr = zeros((5,2)); arr[2,:] .= 1; arr[4, :] .= 1
2-element view(::Matrix{Float64}, 4, :) with eltype Float64:
 1.0
 1.0

julia> backproject(arr, [0, π/2])
6×6 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0  0.0       0.0  0.0       0.0
 0.0  0.0  0.0       0.0  0.0       0.0
 0.0  0.0  2.0       1.0  2.0       0.732051
 0.0  0.0  1.0       0.0  1.0       0.0
 0.0  0.0  2.0       1.0  2.0       0.732051
 0.0  0.0  0.732051  0.0  0.732051  0.0

julia> arr = ones((2,1)); 

julia> backproject(arr, [0], geometry=RadonFlexibleCircle(10, [-3, 3], [0,0]))
10×10 view(::Array{Float64, 3}, :, :, 1) with eltype Float64:
 0.0  0.0  0.0       0.0       0.0        0.0      0.0        0.0       0.0       0.0
 0.0  0.0  0.0       0.0       0.0        0.0      0.0        0.0       0.0       0.0
 0.0  0.0  0.0       0.0       0.335172   1.49876  0.335172   0.0       0.0       0.0
 0.0  0.0  0.0       0.0       1.08455    0.0      1.08455    0.0       0.0       0.0
 0.0  0.0  0.0       0.0       1.08455    0.0      1.08455    0.0       0.0       0.0
 0.0  0.0  0.0       1.00552   0.0790376  0.0      0.0790376  1.00552   0.0       0.0
 0.0  0.0  0.0       1.08455   0.0        0.0      0.0        1.08455   0.0       0.0
 0.0  0.0  0.591307  0.493247  0.0        0.0      0.0        0.493247  0.591307  0.0
 0.0  0.0  0.700352  0.0       0.0        0.0      0.0        0.0       0.700352  0.0
 0.0  0.0  0.0       0.0       0.0        0.0      0.0        0.0       0.0       0.0
```
