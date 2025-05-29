```
scale!(A, b::Number) ≈ A .* b
scale!(M, v::Vector) ≈ A .* v       # M::Matrix
scale!(M, r::Adjoint) ≈ A .* r      # r::RowVector / Transpose etc.
scale!(A, B) ≈ A .* B               # A,B same ndims
```

In-place scaling by a constant or (in the case of a matrix) by a row- or column-vector. For each of these, there is also also `scale_(A, ...)` non-mutating but perhaps accellerated, and `scale0(A, ...)` simple broadcasting.
