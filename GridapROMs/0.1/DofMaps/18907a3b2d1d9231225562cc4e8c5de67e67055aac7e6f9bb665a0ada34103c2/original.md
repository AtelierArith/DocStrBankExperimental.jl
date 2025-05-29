```
slow_index(i,nfast::Integer) -> Any
```

Returns the slow index in a tensor product structure. Suppose we have two matrices `A` and `B` of sizes `Ra × Ca` and `Rb × Rb`. Their kronecker product `AB = A ⊗ B`, of size `RaRb × CaCb`, can be indexed as

`AB[i,j] = A[slow_index(i,RbCb)]B[fast_index(i,RbCb)]`,

where `nfast == RbCb`. In other words, this function converts an index belonging to `AB` to an index belonging to `A`
