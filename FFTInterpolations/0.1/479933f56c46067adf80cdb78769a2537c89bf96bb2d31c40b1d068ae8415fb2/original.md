```
downsample(arr, new_size [, normalize])
```

Downsample an array `arr` to the new size `new_size`. This is calculated by cutting a centered frequency window from the frequency spectrum and going back to real space with an `ifft`. `normalize=true` by default multiplies by an appropriate factor so that  the average intensity stays the same.

# Examples

```jldoctest
julia> downsample([1.0, 0.0, 1.0, 0.0, 1.0, 0.0], [3])
3-element Array{Float64,1}:
 0.5
 0.5
 0.5

julia> downsample([1.0, 0.0, 0.0, 1.0, 0.0, 0.0, 1.0, 0.0, 0.0], [6])
6-element Array{Float64,1}:
  1.0
 -0.3333333333333333
  1.0
 -0.3333333333333333
  1.0
 -0.3333333333333333
```
