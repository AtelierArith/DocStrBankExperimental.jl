```
MPSKit.expectation_value(st::InfiniteMPS, op::Union{InfiniteTransferPEPS,InfiniteTransferPEPO})
MPSKit.expectation_value(st::MultilineMPS, op::Union{MultilineTransferPEPS,MultilineTransferPEPO})
```

単位セル内の各サイトに対して、状態 `st` の転送演算子 `op` の期待値を計算します。
