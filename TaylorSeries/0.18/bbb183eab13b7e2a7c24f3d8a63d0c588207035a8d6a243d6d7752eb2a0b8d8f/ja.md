```
constant_term(a)
```

`Taylor1` と `TaylorN` の定数値（ゼロ次係数）を返します。フォールバック動作は、`a` が `Number` の場合は `a` 自体を返し、`a` が `Vector` の場合は `a[1]` を返します。
