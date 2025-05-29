```
imrotate!(out, arr::AbstractArray, θ; method=:bilinear, midpoint=size(arr) .÷ 2 .+ 1)
```

[`imrotate`](@ref) のインプレースバージョンです。

!!! warning
    `out` の値は上書きされるのではなく、回転操作の値に加算されます！したがって、`out .+ arr == imrotate!(out, arr, θ)` です。

