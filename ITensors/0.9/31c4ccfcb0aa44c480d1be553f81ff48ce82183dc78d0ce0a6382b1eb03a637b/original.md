```
denseblocks(T::ITensor)
```

Make a new ITensor where any blocks which have a sparse format, such as diagonal sparsity, are made dense while still preserving the outer block-sparse structure. This method avoids allocating new data if possible.

For example, an ITensor with DiagBlockSparse storage will have BlockSparse storage afterwards.
