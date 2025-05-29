```
HomalgRowVector(L, R)
```

Construct a (1 x c)-matrix over the ring R with entries in the list L, where c = length(L)

```jldoctest
julia> mat = HomalgRowVector(1:5, ZZ)
[1   2   3   4   5]
```
