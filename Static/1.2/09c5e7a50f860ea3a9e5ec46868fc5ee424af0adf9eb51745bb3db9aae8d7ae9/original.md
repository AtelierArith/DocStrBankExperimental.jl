```
NDIndex(i, j, k...)   -> I
NDIndex((i, j, k...)) -> I
```

A multidimensional index that refers to a single element. Each dimension is represented by a single `Int` or `StaticInt`.

```julia
julia> using Static

julia> i = NDIndex(static(1), 2, static(3))
NDIndex(static(1), 2, static(3))

julia> i[static(1)]
static(1)

julia> i[1]
1

```
