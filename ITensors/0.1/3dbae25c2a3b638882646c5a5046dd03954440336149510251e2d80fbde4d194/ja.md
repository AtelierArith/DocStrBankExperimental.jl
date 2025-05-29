```
Index(qnblocks::Vector{Pair{QN, Int64}}; dir::Arrow = Out,
                                         tags = "",
                                         plev::Int = 0)
```

QNとブロック次元のペアのベクターからQNインデックスを構築します。

注意: 将来的には、すべてのブロックが同じQNを持つことを強制する可能性があります（これにより、ランダムQN ITensorを構築する際の最適化が可能になります）。

# 例

```
Index([QN("Sz", -1) => 1, QN("Sz", 1) => 1]; tags = "i")
```
