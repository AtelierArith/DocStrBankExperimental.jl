```
storage,chunksizes = chunking(v::MFVariable)
storage,chunksizes = chunking(v::MFCFVariable)
```

Return the storage type (`:contiguous` or `:chunked`) and the chunk sizes of the varable `v` corresponding to the first file. If the first file in the collection is chunked then this storage attributes are returned. If not the first file is not contiguous, then multi-file variable is still reported as chunked with chunk size equal to the size of the first variable.
