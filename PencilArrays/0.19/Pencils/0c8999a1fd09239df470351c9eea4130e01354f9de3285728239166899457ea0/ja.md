```
to_local(p::Pencil, global_inds, [order = LogicalOrder()])
```

非順列（論理）グローバルインデックスをローカルインデックスに変換します。

`order = MemoryOrder()` の場合、返されるインデックスは、ペンシル構成 `p` に関連付けられた順列を使用して順列されます。
