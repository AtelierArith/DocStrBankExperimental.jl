````
grid_sample(input::AbstractArray{T, 4}, grid::AbstractArray{T, 4}; padding_mode = :zeros)
grid_sample(input::AbstractArray{T, 5}, grid::AbstractArray{T, 4}; padding_mode = :zeros)

Given `input`, compute output by sampling `input` values at pixel
locations from `grid`. Uses bilinear interpolation to calculate output values.

This implementation assumes the extrema (`-1` and `1`) are considered
as referring to the center points of the input’s corner pixels
(i.e. align corners is `true`).

# Arguments

- `input`: Input array in `(W_in, H_in, [D_in,] C, N)` shape.
- `grid`: Input grid in `(2, W_out, H_out, [D_out,] N)` shape.
    Where for each `(W_out, H_out, [D_out,] N)` grid contains `(x, y [,z])`
    coordinates that specify sampling locations normalized by the `input` shape.

    Therefore, `x`, `y` and [`z`] should have values in `[-1, 1]` range.
    For example, `(x = -1, y = -1, [z = -1])` is the left-top[-front] pixel of `input`,
    and `(x = 1, y = 1, [z = 1])` is the right-bottom-back pixel of `input`.

    Out-of-bound values are handled according to the `padding_mode`.
- `padding_mode`: Out-of-bound padding.
    `:zeros` to use `0` for out-of-bound grid locations.
    `:border` to use border values for out-of-bound grid locations.
    Default is `:zeros`.

# Returns

`(W_out, H_out, [D_out,] C, N)` sampled grid from `input`.

# Examples

In the example below, grid contains two out-of-bound sampling locations,
which are handled differently, depending on the `padding_mode`.

```jldoctest
julia> x = reshape(collect(1.0:4.0), (2, 2, 1, 1))
2×2×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
1.0  3.0
2.0  4.0

julia> grid = Array{Float64}(undef, 2, 3, 2, 1);

julia> grid[:, 1, 1, 1] .= (-3, -1);

julia> grid[:, 2, 1, 1] .= (0, -1);

julia> grid[:, 3, 1, 1] .= (1, -1);

julia> grid[:, 1, 2, 1] .= (-1, 1);

julia> grid[:, 2, 2, 1] .= (0, 1);

julia> grid[:, 3, 2, 1] .= (3, 1);

julia> grid_sample(x, grid; padding_mode=:zeros)
3×2×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
0.0  3.0
1.5  3.5
2.0  0.0

julia> grid_sample(x, grid; padding_mode=:border)
3×2×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
1.0  3.0
1.5  3.5
2.0  4.0
```
````
