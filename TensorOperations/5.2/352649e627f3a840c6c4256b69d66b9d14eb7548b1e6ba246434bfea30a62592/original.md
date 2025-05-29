```
@cutensor tensor_expr
```

Use the GPU to perform all tensor operations, through the use of the cuTENSOR library. This will transfer all arrays to the GPU before performing the requested operations. If the output is an existing host array, the result will be transferred back. If a new array is created (i.e. using `:=`), it will remain on the GPU device and it is up to the user to transfer it back. This macro is equivalent to `@tensor backend=cuTENSORBackend() allocator=CUDAAllocator() tensor_expr`.

!!! note
    This macro requires the cuTENSOR library to be installed and loaded. This can be achieved by running `using cuTENSOR` or `import cuTENSOR` before using the macro.

