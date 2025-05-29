```
ZScore()
```

すべての列にzスコア変換（別名：正規スコア）を適用します。列 `x` のzスコア変換は、平均 `μ` と標準偏差 `σ` を用いて `(x .- μ) ./ σ` で定義されます。

```
ZScore(col₁, col₂, ..., colₙ)
ZScore([col₁, col₂, ..., colₙ])
ZScore((col₁, col₂, ..., colₙ))
```

列 `col₁`, `col₂`, ..., `colₙ` にZScore変換を適用します。

```
ZScore(regex)
```

`regex` に一致する列にZScore変換を適用します。

# 例

```julia
ZScore(1, 3, 5)
ZScore([:a, :c, :e])
ZScore(("a", "c", "e"))
ZScore(r"[ace]")
```
