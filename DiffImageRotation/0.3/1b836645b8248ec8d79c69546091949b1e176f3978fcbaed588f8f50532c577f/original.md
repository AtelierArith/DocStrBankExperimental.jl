```
imrotate!(out, arr::AbstractArray, θ; method=:bilinear, midpoint=size(arr) .÷ 2 .+ 1)
```

In-place version of [`imrotate`](@ref).

!!! warning
    The values in `out` are not overwritten but added to the values of the rotation operation! So `out .+ arr == imrotate!(out, arr, θ)`

