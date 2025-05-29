```
unsafe_free!(a::GPUArray)
```

Release the memory of an array for reuse by future allocations. This operation is performed automatically by the GC when an array goes out of scope, but can be called earlier to reduce pressure on the memory allocator.
