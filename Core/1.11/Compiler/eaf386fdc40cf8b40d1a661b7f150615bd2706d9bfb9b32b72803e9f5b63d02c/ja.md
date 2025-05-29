```
tmerge_field(𝕃::AbstractLattice, a, b) -> nothing or lattice element
```

要素 `a` と `b` のラティス結合をラティス `𝕃` 上で計算します。ここで、`a` と `b` は `PartialStruct` または `Const` のフィールドです。これは、外部ラティス実装が独自のフィールドマージ戦略を提供できるようにするためのオプトインインターフェースです。`nothing` を返す場合、`tmerge(::PartialsLattice, ...)` は、収束に達するために再帰的に `tmerge` を使用しないデフォルトの攻撃的な型マージ実装を使用します。
