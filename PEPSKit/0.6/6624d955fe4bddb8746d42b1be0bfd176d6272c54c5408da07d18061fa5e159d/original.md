```
MPSKit.expectation_value(st::InfiniteMPS, op::Union{InfiniteTransferPEPS,InfiniteTransferPEPO})
MPSKit.expectation_value(st::MultilineMPS, op::Union{MultilineTransferPEPS,MultilineTransferPEPO})
```

Compute expectation value of the transfer operator `op` for the state `st` for each site in the unit cell.
