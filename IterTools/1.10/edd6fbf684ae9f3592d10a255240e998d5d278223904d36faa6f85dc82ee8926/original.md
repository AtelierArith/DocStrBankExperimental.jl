```
takestrict(xs, n::Int)
```

Like `take()`, an iterator that generates at most the first `n` elements of `xs`, but throws an exception if fewer than `n` items are encountered in `xs`.

```jldoctest
julia> collect(takestrict(1:2:11, 3))
3-element Vector{Int64}:
 1
 3
 5
```
