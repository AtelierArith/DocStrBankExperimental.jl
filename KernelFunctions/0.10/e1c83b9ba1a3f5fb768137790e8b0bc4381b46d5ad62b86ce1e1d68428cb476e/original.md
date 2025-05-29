```
ARDTransform(v::AbstractVector)
```

Transformation that multiplies the input elementwise by `v`.

# Examples

```jldoctest
julia> v = rand(10); t = ARDTransform(v); X = rand(10, 100);

julia> map(t, ColVecs(X)) == ColVecs(v .* X)
true
```
