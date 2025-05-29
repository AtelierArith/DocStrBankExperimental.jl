```
splitobs(n::Int; at) -> Tuple
```

Compute the indices for two or more disjoint subsets of the range `1:n` with split sizes determined by `at`.

# Examples

```julia
julia> splitobs(100, at=0.7)
(1:70, 71:100)

julia> splitobs(100, at=(0.1, 0.4))
(1:10, 11:50, 51:100)
```
