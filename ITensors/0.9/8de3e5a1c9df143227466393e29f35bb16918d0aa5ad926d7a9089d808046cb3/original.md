```
diag_itensor([::Type{ElT} = Float64, ]inds)
diag_itensor([::Type{ElT} = Float64, ]inds::Index...)
```

Make a sparse ITensor of element type `ElT` with only elements along the diagonal stored. Defaults to having `zero(T)` along the diagonal.

The storage will have `NDTensors.Diag` type.
