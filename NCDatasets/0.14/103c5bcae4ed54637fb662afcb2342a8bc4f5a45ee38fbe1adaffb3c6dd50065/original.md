```
storage,chunksizes = chunking(v::Variable)
```

Return the storage type (`:contiguous` or `:chunked`) and the chunk sizes of the varable `v`. Note that `chunking` reports the same information as `nc_inq_var_chunking` and therefore [considers variables with unlimited dimension as `:contiguous`](https://github.com/Unidata/netcdf-c/discussions/2224).
