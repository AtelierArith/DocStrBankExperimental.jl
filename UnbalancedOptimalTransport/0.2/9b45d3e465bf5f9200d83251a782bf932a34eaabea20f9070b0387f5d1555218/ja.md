```
DiscreteMeasure(density, [log_density], set) -> DiscreteMeasure
```

[`unbalanced_sinkhorn!`](@ref) および関連関数で使用するための `DiscreteMeasure` オブジェクトを構築します。

  * `density` は厳密に正である必要があります; ゼロ要素は `set` から削除されるべきです
  * `log_density` は `log.(density)` と等しく、省略可能です（この場合、自動的に計算されます）
  * `set` はコレクションであり、`density[i]` は要素 `set[i]` が発生する確率です（ここで `i ∈ eachindex(density, set)`）。
