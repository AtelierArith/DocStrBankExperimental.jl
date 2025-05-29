```
empty!!(collection) -> collection′
```

# 例

```jldoctest
julia> using BangBang

julia> empty!!((1, 2, 3))
()

julia> empty!!((a=1, b=2, c=3))
NamedTuple()

julia> xs = [1, 2, 3];

julia> empty!!(xs)
Int64[]

julia> xs
Int64[]

julia> using StaticArrays: SVector

julia> @assert empty!!(SVector(1, 2)) == SVector{0, Int}()
```
