```
pointwisemult!(w::CeedVector, x::CeedVector, y::CeedVector)
```

Overwrite `w` with `x .* y`. Any subset of x, y, and w may be the same vector. Returns `w`.
