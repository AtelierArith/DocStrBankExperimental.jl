```
InfiniteTransferPEPO(T::InfinitePEPS, O::InfinitePEPO, dir, row)
```

Constructs a transfer operator corresponding to a single row of a partition function representing the expectation value of `O` for the state `T`. The partition function is first rotated such that the direction `dir` faces north, after which its `row`th row from the north is selected.
