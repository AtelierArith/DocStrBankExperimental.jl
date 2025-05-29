```
flatten(a)
```

Takes a collection of collections `a` and returns a collection containing all the elements of the subcollecitons of `a`. Equivalent to `mapmany(idenity, a)`.

# Example

```jldoctest
julia> flatten([1:1, 1:2, 1:3])
6-element Array{Int64,1}:
 1
 1
 2
 1
 2
 3
```
