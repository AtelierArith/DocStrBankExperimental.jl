```
multiplot([pos], plts, args...; kwargs...)
```

同じデータを使って複数のプロットを作成します。

同じデータを取る `plts` の任意の組み合わせがサポートされています。一般的な例には以下が含まれます：

  * `(lines, band)`,
  * `(scatter, rangebars)`,
  * `(scatter, rangebars, rangebars => (;direction=:x))`
