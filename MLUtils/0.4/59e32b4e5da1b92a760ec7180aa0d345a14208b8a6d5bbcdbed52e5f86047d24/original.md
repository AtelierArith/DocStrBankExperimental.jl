```
slidingwindow(data; size, stride=1, obsdim=nothing) -> SlidingWindow
```

Return a vector-like view of the `data` for which each element is a fixed size "window" of `size` adjacent observations. 

`stride` specifies the distance between the start elements of each adjacent window. The default value is 1. Note that only complete windows are included in the output, which implies that it is possible for excess observations to be omitted from the view.

`obsdim` specifies the dimension along which the observations are indexed for the data types that support it (e.g. arrays).  By default, the observations are indexed along the last dimension of the data. If `obsdim` is specified it will be  passed to `obsview` to get a view of the data along that dimension.

Note that the windows are not materialized at construction time.  To actually get a copy of the data at some window use indexing or [`getobs`](@ref).

When indexing the data is accessed as `getobs(data, idxs)`, with `idxs` an appropriate range of indexes.

# Examples

```jldoctest
julia> s = slidingwindow(11:30, size=6)
slidingwindow(20-element UnitRange{Int64}, size=6, stride=1)

julia> s[1]  # == getobs(data, 1:6)
11:16

julia> s[2]  # == getobs(data, 2:7)
12:17
```

The optional parameter `stride` can be used to specify the distance between the start elements of each adjacent window. By default the stride is equal to 1.

```jldoctest
julia> s = slidingwindow(11:30, size=6, stride=3)
slidingwindow(20-element UnitRange{Int64}, size=6, stride=3)

julia> for w in s; println(w); end
11:16
14:19
17:22
20:25
23:28
```
