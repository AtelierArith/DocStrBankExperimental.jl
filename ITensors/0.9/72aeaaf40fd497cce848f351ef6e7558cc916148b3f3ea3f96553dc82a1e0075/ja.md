```
Index(qnblocks::Vector{Pair{QN, Int64}}, tags; plev::Integer = 0)
```

QNインデックスをQNとブロック次元のペアのベクターから構築します。

# 例

```
i = Index([QN("Sz", -1) => 1, QN("Sz", 1) => 1], "i")
idag = dag(i) # 矢印の方向が反転した同じインデックス
```
