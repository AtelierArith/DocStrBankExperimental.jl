```
VecRange{N}(i::Int)
```

Analogous to `UnitRange` but for loading SIMD vector of width `N` at index `i`.

# Examples

```jldoctest
julia> xs = ones(4);
julia> xs[VecRange{4}(1)]  # calls `vload(Vec{4,Float64}, xs, 1)`
<4 x Float64>[1.0, 1.0, 1.0, 1.0]
```
