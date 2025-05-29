```
a  == b
a == 1.0
```

Returns the Boolean expression a == b (arithmetic equivalence). Use dot broadcasting for vector-valued and matrix-valued expressions.

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
a .== b
```

**Note:** To test whether two `AbstractExpr`s are eqivalent (in the sense that all properties are equal, not in the shared-memory-location sense of `===`), use `isequal`.
