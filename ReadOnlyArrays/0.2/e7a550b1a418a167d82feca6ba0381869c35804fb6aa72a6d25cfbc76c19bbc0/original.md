```
ReadOnlyArray(X)
```

Returns a read-only view into the parent array `X`.

# Examples

```jldoctest
julia> a = [1 2; 3 4]
2×2 Array{Int64,2}:
 1  2
 3  4

julia> r = ReadOnlyArray(a)
2×2 ReadOnlyArray{Int64,2,Array{Int64,2}}:
 1  2
 3  4

julia> r[1]
1

julia> r[1] = 10
CanonicalIndexError: setindex! not defined for ReadOnlyArray{Int64,2,Array{Int64,2}}
[...]
```
