```
ScaleTransform(l::Real)
```

Transformation that multiplies the input elementwise with `l`.

# Examples

```jldoctest
julia> l = rand(); t = ScaleTransform(l); X = rand(100, 10);

julia> map(t, ColVecs(X)) == ColVecs(l .* X)
true
```
