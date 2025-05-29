```
initialize_mps(
    f=randn,
    T=scalartype(O),
    O::Union{InfiniteTransferPEPS,InfiniteTransferPEPO},
    virtualspaces::AbstractArray{<:ElementarySpace,1}
)
initialize_mps(
    f=randn,
    T=scalartype(O),
    O::Union{MultilineTransferPEPS,MultilineTransferPEPO},
    virtualspaces::AbstractArray{<:ElementarySpace,2}
)
```

転送演算子 `O` の境界 MPS を、単位セルと一致する仮想空間の配列を指定して初期化します。
