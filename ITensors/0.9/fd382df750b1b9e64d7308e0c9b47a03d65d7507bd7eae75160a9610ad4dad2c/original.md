```
diag_itensor([ElT::Type, ]x::Number, inds...)
diagitensor([ElT::Type, ]x::Number, inds...)
```

Make a sparse ITensor with non-zero elements only along the diagonal. In general, the diagonal elements will be set to the value `x` and the ITensor will have element type `eltype(x)`, unless specified explicitly by `ElT`. The storage will have `NDTensors.Diag` type.

In the case when `x isa Union{Int, Complex{Int}}`, by default it will be converted to `float(x)`. Note that this behavior is subject to change in the future.
