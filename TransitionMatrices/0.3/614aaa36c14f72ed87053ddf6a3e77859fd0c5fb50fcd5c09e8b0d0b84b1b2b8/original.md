Iterator for the order-degree pairs of the given maximum order `nₘₐₓ`.

Example of `nₘₐₓ=2`:

```jldoctest
julia> collect(OrderDegreeIterator(2))
8-element Vector{Tuple{Int64, Int64}}:
 (1, -1)
 (1, 0)
 (1, 1)
 (2, -2)
 (2, -1)
 (2, 0)
 (2, 1)
 (2, 2)
```
