```
TriMatrix{T}(layout::TriLayout, m::AbstractMatrix; diag=zero(T))
TriMatrix(layout::TriLayout, m::AbstractMatrix; [diag])
```

Create a `TriMatrix` by copying data from a square matrix `m`.

If unspecified `T` defaults to `eltype(m)`.
