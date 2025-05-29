```
AMORS.solve(f, x0, y0) -> (status, x, y)
```

AMORS戦略をアウトオブプレイスで適用します。つまり、初期変数 `x0` と `y0` を変更しません。メソッドの説明については [`AMORS.solve!`](@ref) を参照してください。

メソッド `Base.similar` と `Base.copyto!` は、`x0` と `y0` と同じ型のオブジェクトに適用可能でなければなりません。
