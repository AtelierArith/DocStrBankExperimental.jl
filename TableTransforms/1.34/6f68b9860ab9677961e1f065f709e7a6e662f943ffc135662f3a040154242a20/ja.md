```
Reject(col₁, col₂, ..., colₙ)
Reject([col₁, col₂, ..., colₙ])
Reject((col₁, col₂, ..., colₙ))
```

列 `col₁`, `col₂`, ..., `colₙ` を破棄する変換。

```
Reject(regex)
```

`regex` に一致する列を破棄します。

# 例

```julia
Reject(:b, :d, :f)
Reject(["b", "d", "f"])
Reject((2, 4, 6))
Reject(r"[bdf]")
```
