```
TriMatrix{T}(layout::TriLayout, undef, n::Integer; diag=zero(T))
TriMatrix(layout::TriLayout, undef, n::Integer; diag=0.)
```

Create an uninitialized `n` by `n` `TriMatrix`.

`T` defaults to `Float64` if not specified.
