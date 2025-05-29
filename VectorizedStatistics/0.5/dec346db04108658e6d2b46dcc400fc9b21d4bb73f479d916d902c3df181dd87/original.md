```julia
vextrema(A; dims)
```

Find the maximum and minimum of `A`, optionally along the dimensions specified by `dims`. As `Base.extrema`, but vectorized.

## Examples

julia> A = reshape(Vector(1:2:16), (2,2,2)) 2×2×2 Array{Int64, 3}:  [:, :, 1] =   1  5   3  7

[:, :, 2] =    9  13   11  15

julia> extrema(A, dims = (1,2)) 1×1×2 Array{Tuple{Int64, Int64}, 3}:  [:, :, 1] =   (1, 7)

[:, :, 2] =   (9, 15)
