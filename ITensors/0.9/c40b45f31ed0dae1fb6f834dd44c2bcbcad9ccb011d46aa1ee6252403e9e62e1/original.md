```
emptyITensor([::Type{ElT} = EmptyNumber, ]inds)
emptyITensor([::Type{ElT} = EmptyNumber, ]inds::QNIndex...)
```

Construct an ITensor with `NDTensors.BlockSparse` storage of element type `ElT` with the no blocks.

If `ElT` is not specified it defaults to `NDTensors.EmptyNumber`.
