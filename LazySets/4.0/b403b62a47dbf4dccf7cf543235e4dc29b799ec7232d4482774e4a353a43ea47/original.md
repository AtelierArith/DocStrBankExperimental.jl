# Extended help

```
isequivalent(X::LazySet, Y::LazySet)
```

### Algorithm

The default implementation first checks `X ≈ Y`, which returns `true` if and only if `X` and `Y` have the same base type and approximately the same values. If that fails, the implementation checks the double inclusion `X ⊆ Y && Y ⊆ X`.

### Examples

```jldoctest
julia> X = BallInf([0.1, 0.2], 0.3);

julia> Y = convert(HPolytope, X);

julia> X == Y
false

julia> isequivalent(X, Y)
true
```
