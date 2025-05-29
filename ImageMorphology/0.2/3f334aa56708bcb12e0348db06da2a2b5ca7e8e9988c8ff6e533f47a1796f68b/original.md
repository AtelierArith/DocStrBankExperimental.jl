```
imge = erode(img, [region])
```

perform a min-filter over nearest-neighbors. The default is 8-connectivity in 2d, 27-connectivity in 3d, etc. You can specify the list of dimensions that you want to include in the connectivity, e.g., `region = [1,2]` would exclude the third dimension from filtering.

# Examples

```jldoctest; setup = :(using ImageMorphology), filter = r"Array{Float64,2}|Matrix{Float64}"
julia> img = zeros(5, 5); img[2:4, 2:4] .= 1.; img
5×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> erode(img)
5×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> erode(img, 1)
5×5 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  1.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
```
