```
A = StreamingContainer{T}(f!, parent, streamingaxes::Axis...)
```

An array-like object possessing one or more axes for which changing "slices" may be expensive or subject to restrictions. A canonical example would be an AVI stream, where addressing pixels within the same frame is fast but jumping between frames might be slow.

Here's a simple example of dividing by the mean of each slice of an image before returning values.

```
A = AxisArrays.AxisArray(reshape(1:36, 3, 3, 4))

function f!(buffer, slice)
    meanslice = mean(slice)
    buffer .= slice./meanslice
end

B = StreamingContainer{Float64}(f!, A, AxisArrays.axes(A)[3])

julia> A[:,:,1]
3×3 AxisArray{Int64,2,Array{Int64,2},Tuple{Axis{:row,Base.OneTo{Int64}},Axis{:col,Base.OneTo{Int64}}}}:
 1  4  7
 2  5  8
 3  6  9

julia> B[:,:,1]
3×3 Array{Float64,2}:
 0.2  0.8  1.4
 0.4  1.0  1.6
 0.6  1.2  1.8
```

The user-provided `f!` function should take arguments:

```
f!(buffer, slice)
```

Where `buffer` will be an empty array that can hold a slice of your series, and `slice` will hold the current input slice.

It's worth noting that `StreamingContainer` is *not* a subtype of `AbstractArray`, but that much of the array interface (`eltype`, `ndims`, `axes`, `size`, `getindex`, and `IndexStyle`) is supported. A StreamingContainer `A` can be built from an AxisArray, but it may also be constructed from other "parent" objects, even non-arrays, as long as they support the same functions. In either case, the parent should also support the standard AxisArray functions `axes`, `axisnames`, `axisvalues`, and `axisdim`; this support will be extended to the `StreamingContainer`.

Additionally, a StreamingContainer `A` supports

```
getindex!(dest, A, axt::Axis{:time}, ...)
```

to obtain slices along the streamed axes (here it is assumed that `:time` is a streamed axis of `A`). You can implement this directly (dispatching on the parameters of `A`), or (if the parent is an `AbstractArray`) rely on the fallback

```
A.getindex!(dest, view(parent, axs...))
```

where `A.getindex! = f!` as passed as an argument at construction. `dest` should have dimensionality `ndims(parent)-length(streamingaxes)`.

Optionally, define [`StreamIndexStyle(typeof(parent),typeof(f!))`](@ref).
