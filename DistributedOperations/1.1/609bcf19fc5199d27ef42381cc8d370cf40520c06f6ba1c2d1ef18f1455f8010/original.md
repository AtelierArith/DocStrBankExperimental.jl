```
y = reduce!(x::TypeFutures[, reducemethod!=DistributedOperations.paralleloperations_reduce!])
```

Parallel reduction of `x::TypeFutures` using `reducemethod!`.  By default, the reduction is a mutating in-place element-wise addition, such that `y=localpart(x)`.

# Example

```
using Distributed
addprocs(2)
@everywhere using DistributedOperations
x = ArrayFutures(Float64, (3,))
fill!(x, 1, workers())
y = reduce!(x)
y ≈ [2.0,2.0,2.0] # true
localpart(x) ≈ [2.0,2.0,2.0] # true
rmprocs(workers())
```
