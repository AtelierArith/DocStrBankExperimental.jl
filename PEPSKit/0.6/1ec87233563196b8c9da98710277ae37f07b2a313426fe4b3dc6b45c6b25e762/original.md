```
leading_boundary(
    st::InfiniteMPS, op::Union{InfiniteTransferPEPS,InfiniteTransferPEPO}, alg, [env]
)
leading_boundary(
    st::MPSMulitline, op::Union{MultilineTransferPEPS,MultilineTransferPEPO}, alg, [env]
)
```

Approximate the leading boundary MPS eigenvector for the transfer operator `op` using `st` as initial guess.
