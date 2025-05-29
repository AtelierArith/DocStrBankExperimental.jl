```
(xg, yg, ...) = ndgrid(M, N, ...)
```

Shorthand for `ndgrid(1:M, 1:N, ...)`.

# Example

```jldoctest
julia> ndgrid(2,3)
([1 1 1; 2 2 2], [1 2 3; 1 2 3])
```
