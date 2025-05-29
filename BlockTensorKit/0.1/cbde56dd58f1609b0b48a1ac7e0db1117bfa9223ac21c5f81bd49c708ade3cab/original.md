```
spzeros(T::Type, W::TensorMapSumSpace)
spzeros(T, W, nonzero_inds)
```

Construct a sparse blocktensor with entries compatible with type `T` and space `W`. By default, the tensor will be empty, but nonzero entries can be specified by passing a tuple of indices `nonzero_inds`.
