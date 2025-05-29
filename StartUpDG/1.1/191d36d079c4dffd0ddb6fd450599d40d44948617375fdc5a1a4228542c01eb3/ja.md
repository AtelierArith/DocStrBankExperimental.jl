```
function sparse_low_order_SBP_operators(rd; factor=1.01)
```

与えられた `RefElemData` に基づいてスパース低次SBP演算子を構築します。一般化された部分和（GSBP）特性を満たす演算子 `Qrst..., E ≈ Vf * Pq` を返します：

```
    `Q_i + Q_i^T = E' * B_i * E`
```

`factor` は、ノードが隣接ノードと見なされるためにどれだけ近くなければならないかを決定するスケーリングです。
