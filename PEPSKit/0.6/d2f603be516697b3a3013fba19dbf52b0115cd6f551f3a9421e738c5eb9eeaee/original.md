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

Inialize a boundary MPS for the transfer operator `O` by specifying an array of virtual spaces consistent with the unit cell.
