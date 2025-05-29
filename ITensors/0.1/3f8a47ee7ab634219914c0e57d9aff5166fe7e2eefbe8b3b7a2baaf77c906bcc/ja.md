```
Index(qnblocks::Vector{Pair{QN, Int64}}, tags; dir::Arrow = Out,
                                               plev::Int = 0)
```

QNとブロック次元のペアのベクターからQNインデックスを構築します。

# 例

```
Index([QN("Sz", -1) => 1, QN("Sz", 1) => 1], "i"; dir = In)
```
