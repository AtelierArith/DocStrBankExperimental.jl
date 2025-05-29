```
Interquartile()
```

テーブルのすべての列にインタクォータイル変換を適用します。インタクォータイル変換は `LowHigh(low=0.25, high=0.75)` と同等です。

```
Interquartile(col₁, col₂, ..., colₙ)
Interquartile([col₁, col₂, ..., colₙ])
Interquartile((col₁, col₂, ..., colₙ))
```

列 `col₁`, `col₂`, ..., `colₙ` にインタクォータイル変換を適用します。

```
Interquartile(regex)
```

`regex` に一致する列にインタクォータイル変換を適用します。

# 例

```julia
Interquartile(1, 3, 5)
Interquartile([:a, :c, :e])
Interquartile(("a", "c", "e"))
Interquartile(r"[ace]")
```

他にも [`LowHigh`](@ref) を参照してください。
