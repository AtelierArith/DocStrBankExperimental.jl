```
datapadded = PaddedView(fillvalue, data, padded_axes)
datapadded = PaddedView(fillvalue, data, padded_axes, data_axes)
datapadded = PaddedView(fillvalue, data, sz)
datapadded = PaddedView(fillvalue, data, sz, first_datum)
datapadded = PaddedView{T}(args...)
```

Create a padded version of the array `data`, where any elements within the span of `padded_axes` not assigned in `data` will have value `fillvalue`.

Supply `data_axes` to specify an alterate set of axes for `data`, effectively relocating `data` to a different set of indices. This is shorthand for

```
offsetdata = OffsetArray(data, data_axes)
datapadded = PaddedView(fillvalue, offsetdata, padded_axes)
```

using the [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl) package.

Alternately, the padded array size `sz` can be specified, in which case `datapadded` starts indexing at 1. One may optionally specify the location of the `[1, 1, ...]` element of `data` with `first_datum`. Specifically, `datapadded[first_datum...]` corresponds to `data[1, 1, ...]`. `first_datum` defaults to all-1s.

The view eltype `T` is optional. If not specified, then in most cases, `T` is inferred to be `eltype(data)`. In cases when `fillvalue` can't be converted to `eltype(data)`, `T` will be promoted the one that does. For example, when `fillvalue == nothing` and `eltype(data) == Float32`, the inferred eltype `T` will be `Union{Nothing, Float32}`.

# Example

```jldoctest
julia> using PaddedViews

julia> a = collect(reshape(1:9, 3, 3))
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> PaddedView(-1, a, (4, 5))
4×5 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(4), Base.OneTo(5))) with eltype Int64:
  1   4   7  -1  -1
  2   5   8  -1  -1
  3   6   9  -1  -1
 -1  -1  -1  -1  -1

julia> PaddedView(-1, a, (1:5,1:5), (2:4,2:4))
5×5 PaddedView(-1, OffsetArray(::Matrix{Int64}, 2:4, 2:4), (1:5, 1:5)) with eltype Int64 with indices 1:5×1:5:
 -1  -1  -1  -1  -1
 -1   1   4   7  -1
 -1   2   5   8  -1
 -1   3   6   9  -1
 -1  -1  -1  -1  -1

julia> PaddedView(-1, a, (0:4, 0:4))
5×5 PaddedView(-1, ::Matrix{Int64}, (0:4, 0:4)) with eltype Int64 with indices 0:4×0:4:
 -1  -1  -1  -1  -1
 -1   1   4   7  -1
 -1   2   5   8  -1
 -1   3   6   9  -1
 -1  -1  -1  -1  -1

julia> PaddedView(-1, a, (5,5), (2,2))
5×5 PaddedView(-1, OffsetArray(::Matrix{Int64}, 2:4, 2:4), (Base.OneTo(5), Base.OneTo(5))) with eltype Int64:
 -1  -1  -1  -1  -1
 -1   1   4   7  -1
 -1   2   5   8  -1
 -1   3   6   9  -1
 -1  -1  -1  -1  -1
```
