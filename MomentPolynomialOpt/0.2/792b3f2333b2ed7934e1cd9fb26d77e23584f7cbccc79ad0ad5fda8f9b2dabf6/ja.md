```julia
v, M = minimize(f, [e1, e2, ...], [p1, p2, ...], X, d, optimizer)
```

制約 $e_i=0$ および $p_i \geq 0$ の下で `f` の下限を計算します。変数 `X` のモーメントに対する次数 `d` の緩和とオプティマイザ `optimizer` を使用します。

[`optimize`](@ref) を参照してください。
