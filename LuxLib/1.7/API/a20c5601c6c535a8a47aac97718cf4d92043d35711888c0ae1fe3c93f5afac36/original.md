```
batched_matmul(x, y)
```

Computes the batched matrix multiplication of `x` and `y`.  For more details see the NNlib documentation on `NNlib.batched_mul`. This function is mostly a wrapper around `batched_mul` but attempts to be faster on CPUs.

!!! tip "Load `LoopVectorization.jl` to get faster batched matrix multiplication"
    On CPUs loading LoopVectorization adds faster implementations of batched matrix multiplication.

