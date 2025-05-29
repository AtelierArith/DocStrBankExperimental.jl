```
evaluate(a, [vals]; sorting::Bool=true)
```

`TaylorN` 多項式 `a` を `vals` で評価します。`vals` が省略された場合、ゼロで評価されます。キーワードパラメータ `sorting` を使用すると、追加される項を（`abs2` による昇順で）ソートしないようにできます。

`a(vals)` の構文は `evaluate(a, vals)` と同等であり、`a()` は `evaluate(a)` と同等です；`a(b::Bool, x)` は `evaluate(a, x, sorting=b)` に対応します。
