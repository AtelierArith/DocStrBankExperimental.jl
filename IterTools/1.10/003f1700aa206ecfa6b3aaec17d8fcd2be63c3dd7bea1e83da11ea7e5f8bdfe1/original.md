```
firstrest(xs) -> (f, r)
```

Return the first element and an iterator of the rest as a tuple.

See also: `Base.Iterators.peel`.

```jldoctest
julia> f, r = firstrest(1:3);

julia> f
1

julia> collect(r)
2-element Vector{Int64}:
 2
 3
```
