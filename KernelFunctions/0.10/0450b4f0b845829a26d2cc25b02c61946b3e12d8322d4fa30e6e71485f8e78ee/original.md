```
FunctionTransform(f)
```

Transformation that applies function `f` to the input.

Make sure that `f` can act on an input. For instance, if the inputs are vectors, use `f(x) = sin.(x)` instead of `f = sin`.

# Examples

```jldoctest
julia> f(x) = sum(x); t = FunctionTransform(f); X = randn(100, 10);

julia> map(t, ColVecs(X)) == ColVecs(sum(X; dims=1))
true
```
