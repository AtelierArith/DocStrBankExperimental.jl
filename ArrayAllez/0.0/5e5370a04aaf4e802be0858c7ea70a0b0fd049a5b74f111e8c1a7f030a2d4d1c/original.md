```
iscale!(A, b::Number) ≈ A ./ b
iscale!(A, v::Vector) ≈ A ./ v      # A::Matrix
iscale!(A, r::Adjoint) ≈ A ./ r     # r::RowVector / Transpose etc.
iscale!(A, B) ≈ A ./ B
```

For each of these, there is also `iscale_(A, ...)` non-mutating but perhaps accellerated, and `iscale0(A, ...)` simple broadcasting. Finally there is `iscale!!(A, x)` which mutate both arguments, wihch may be a terrible idea.
