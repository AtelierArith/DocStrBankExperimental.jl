```
mapmany(f, a...)
```

Like `map`, but `f(x)` for each `x ∈ a` may return an arbitrary number of values to insert into the output.

# Example

```jldoctest
julia> mapmany(x -> 1:x, [1,2,3])
6-element Array{Int64,1}:
 1
 1
 2
 1
 2
 3
```
