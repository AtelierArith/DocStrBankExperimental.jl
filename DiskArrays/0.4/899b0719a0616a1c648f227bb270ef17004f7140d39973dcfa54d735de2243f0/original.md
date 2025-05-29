```
cache(A::AbstractArray; maxsize=1000, mmap=false)
```

Wrap internal disk arrays with `CacheDiskArray`.

This function is intended to be extended by package that want to re-wrap the disk array afterwards, such as YAXArrays.jl or Rasters.jl.
