```
supports_missings_measure(atomic_measure)
```

新しい測定値 `measure` を返します。この測定値は `atomic_measure` と同じ動作を持ちますが、`measure(ŷ, y, args...)` のような呼び出しや [`measurements`](@ref) の適用において `ŷ` または `y` の値として `missing` をサポートします。欠損値はラップされた測定値によって伝播されます（ただし、その後のラッピングや集約ではスキップされる場合があります）。
