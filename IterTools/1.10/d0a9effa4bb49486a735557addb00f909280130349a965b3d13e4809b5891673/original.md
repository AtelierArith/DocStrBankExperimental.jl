```
takewhile(cond, xs)
```

An iterator that yields values from the iterator `xs` as long as the predicate `cond` is true.

```jldoctest
julia> collect(takewhile(x-> x^2 < 10, 1:100))
3-element Vector{Int64}:
 1
 2
 3
```
