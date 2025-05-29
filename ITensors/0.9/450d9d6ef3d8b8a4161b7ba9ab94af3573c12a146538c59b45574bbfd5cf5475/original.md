```
diag_itensor([ElT::Type, ]v::AbstractVector, inds...)
diagitensor([ElT::Type, ]v::AbstractVector, inds...)
```

Make a sparse ITensor with non-zero elements only along the diagonal. In general, the diagonal elements will be those stored in `v` and the ITensor will have element type `eltype(v)`, unless specified explicitly by `ElT`. The storage will have `NDTensors.Diag` type.

In the case when `eltype(v) isa Union{Int, Complex{Int}}`, by default it will be converted to `float(v)`. Note that this behavior is subject to change in the future.

The version `diag_itensor` will never output an ITensor whose storage data is an alias of the input vector data.

The version `diagitensor` might output an ITensor whose storage data is an alias of the input vector data in order to minimize operations.
