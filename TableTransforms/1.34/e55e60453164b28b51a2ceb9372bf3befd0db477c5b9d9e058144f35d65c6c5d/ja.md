```
AbsoluteUnits()
AbsoluteUnits(:)
```

すべての列の単位を絶対単位に変換します。

```
AbsoluteUnits(col₁, col₂, ..., colₙ)
AbsoluteUnits([col₁, col₂, ..., colₙ])
AbsoluteUnits((col₁, col₂, ..., colₙ))
```

選択した列 `col₁`, `col₂`, ..., `colₙ` の単位を絶対単位に変換します。

```
AbsoluteUnits(regex)
```

`regex` に一致する列の単位を絶対単位に変換します。

# 例

```julia
AbsoluteUnits()
AbsoluteUnits([2, 3, 5])
AbsoluteUnits([:b, :c, :e])
AbsoluteUnits(("b", "c", "e"))
AbsoluteUnits(r"[bce]")
```
