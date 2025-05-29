```
leading_boundary(
    st::InfiniteMPS, op::Union{InfiniteTransferPEPS,InfiniteTransferPEPO}, alg, [env]
)
leading_boundary(
    st::MPSMulitline, op::Union{MultilineTransferPEPS,MultilineTransferPEPO}, alg, [env]
)
```

転送演算子 `op` のためのリーディングバウンダリー MPS 固有ベクトルを、初期推測として `st` を使用して近似します。
