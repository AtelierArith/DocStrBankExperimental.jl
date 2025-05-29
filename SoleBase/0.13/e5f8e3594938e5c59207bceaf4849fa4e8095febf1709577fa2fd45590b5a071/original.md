```
movingwindow(vec::AbstractVector; kwargs...)::AbstractVector{UnitRange{Int}}
movingwindow(npoints::Integer; kwargs...)::AbstractVector{UnitRange{Int}}
```

Return a certain number of equally-spaced windows (i.e., vector of integer indices), used for slicing a vector `vec` (or a vector of `npoints` values).

```
movingwindow(f::Base.Callable, vec::AbstractVector; kwargs...)::AbstractVector
```

Return the `map` of `f` over the window slicing of `vec`.

As for the keyword arguments, different flavors of this function are available, according to different use cases.

# Fixed-size windows

```
function movingwindow(
    npoints::Integer;
    window_size::Union{Nothing,Real} = nothing,
    window_step::Union{Nothing,Real} = nothing,
    # Optional arguments
    landmark::Union{Integer,Nothing} = nothing,
    allow_landmark_position::Tuple{<:AbstractFloat,<:AbstractFloat} = (0.0, 1.0),
    kwargs...
)::AbstractVector{UnitRange{Int}}
```

Return windows of length `window_size`, with a step between consecutive windows of `window_step`. When the `window_step` is a floating point number, the step within the returned windows is not constant, but fluctuates around `window_step`.

When a `landmark::Integer` point is specified to the function, only windows containing the landmark will be returned. For example, with `npoints=100` and `landmark=50`, all the windows will contain `50`. It is also possible to specify the range for the relative position of the landmark within the windows using `allow_landmark_position`.

# Fixed number of windows

```
function movingwindow(
    npoints::Integer;
    nwindows::Union{Nothing,Integer} = nothing,
    relative_overlap::Union{Nothing,AbstractFloat} = nothing,
    kwargs...
)::AbstractVector{UnitRange{Int}}
```

Compute `nwindows` windows, with consecutive windows overlapping by a portion equal to `relative_overlap`.

# Fixed number of fixed-sized windows

```
function movingwindow(
    npoints::Integer;
    nwindows::Union{Nothing,Integer} = nothing,
    window_size::Union{Nothing,Real} = nothing,
    kwargs...
)::AbstractVector{UnitRange{Int}}
```

Compute `nwindows` windows of length `window_size`.

# Examples

TODO

Compute windows of length `window_size`, with consecutive windows being shifted by `window_step` units.
