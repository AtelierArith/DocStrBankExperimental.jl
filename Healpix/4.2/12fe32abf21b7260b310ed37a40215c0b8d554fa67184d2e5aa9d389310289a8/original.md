```
boundariesRing(resol::Resolution, pix, step, T::Type{<:Real})
boundariesRing!(resol::Resolution, pix, step, buf::Matrix{T}) where {T <: Real}
```

Compute a set of directions (3D vectors) along the boundaries of a given pixel in the RING scheme at some resolution.

The function `boundariesRing` returns a $N \times 3$ matrix of type `T` containing $N$ vectors pointing towards the border of the pixel with index `pix` in RING scheme. Each edge of the pixel contains `step` points, and, as every pixel has a diamond-like shape with four edges, the number $N$ is equal to `4 * step`.

If you plan to call this function again and again, you should allocate your own matrix with the results and call `boundariesRing!`, which accepts the parameter `buf` where the result will be stored. The shape of this matrix must be `(4step, 3)`, for instance, and its element can be left undefined:

```julia
step = 10
buf = Matrix{Float64}(undef, 4step, 3)
boundariesRing!(res, pixidx, step, buf)  # This sets `buf`
```

# Examples

Here we show how to use `boundariesRing` and `boundariesRing!` together to avoid allocating a matrix twice.

```julia-repl
julia> matr = boundariesRing(Resolution(16), 534, 2, Float16)
8×3 Matrix{Float16}:
 0.3535  -0.6123  0.707
 0.3525  -0.6353  0.687
 0.3513  -0.657   0.6665
 0.3762  -0.664   0.646
 0.4014  -0.6694  0.625
 0.4084  -0.645   0.646
 0.414   -0.6196  0.6665
 0.3843  -0.6167  0.687

julia> boundariesRing!(Resolution(16), 535, 2, matr)  # Reuse `matr`

julia> matr
8×3 Matrix{Float16}:
 0.4158  -0.5723  0.707
 0.415   -0.596   0.687
 0.414   -0.6196  0.6665
 0.4397  -0.624   0.646
 0.465   -0.627   0.625
 0.4697  -0.602   0.646
 0.473   -0.576   0.6665
 0.4446  -0.5747  0.687
```
