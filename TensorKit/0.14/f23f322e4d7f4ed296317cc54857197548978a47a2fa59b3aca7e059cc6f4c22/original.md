```
dim(t::AbstractTensorMap) -> Int
```

The total number of free parameters of a tensor, discounting the entries that are fixed by symmetry. This is also the dimension of the `HomSpace` on which the `TensorMap` is defined.
