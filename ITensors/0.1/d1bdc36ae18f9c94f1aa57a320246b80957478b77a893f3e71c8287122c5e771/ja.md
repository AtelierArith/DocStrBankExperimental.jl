```
Index(qnblocks::Pair{QN, Int64}...; dir::Arrow = Out,
                                    tags = "",
                                    plev::Int = 0)
```

QNインデックスをQNとブロック次元のペアのリストから構築します。

# 例

```
Index(QN("Sz", -1) => 1, QN("Sz", 1) => 1; tags = "i")
```
