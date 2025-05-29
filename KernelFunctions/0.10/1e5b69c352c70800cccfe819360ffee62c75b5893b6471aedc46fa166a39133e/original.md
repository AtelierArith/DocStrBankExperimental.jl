```
ChainTransform(transforms)
```

Transformation that applies a chain of transformations `ts` to the input.

The transformation `first(ts)` is applied first.

# Examples

```jldoctest
julia> l = rand(); A = rand(3, 4); t1 = ScaleTransform(l); t2 = LinearTransform(A);

julia> X = rand(4, 10);

julia> map(ChainTransform([t1, t2]), ColVecs(X)) == ColVecs(A * (l .* X))
true

julia> map(t2 ∘ t1, ColVecs(X)) == ColVecs(A * (l .* X))
true
```
