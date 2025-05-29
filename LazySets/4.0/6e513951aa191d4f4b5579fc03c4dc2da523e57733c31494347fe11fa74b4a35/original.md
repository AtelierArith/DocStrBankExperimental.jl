# Extended help

```
is_interior_point(v::AbstractVector{<:Real}, X::LazySet; [kwargs]...)
```

### Algorithm

The default implementation determines `v ∈ interior(X)` with error tolerance `ε` by checking whether a `Ballp` of norm `p` with center `v` and radius `ε` is contained in `X`.
