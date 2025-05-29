```
differentiate(expr::Expression, var::Variable, k = 1)
differentiate(expr::AbstractVector{Expression}, var::Variable, k = 1)
```

与えられた変数 `var` に関して `expr` の `k` 番目の導関数を計算します。

```
differentiate(expr::Expression, vars::AbstractVector{Variable})
```

与えられた変数 `vars` に関して `expr` の偏導関数を計算します。偏導関数を含む `Vector` を返します。

```
differentiate(exprs::AbstractVector{Expression}, vars::AbstractVector{Variable})
```

与えられた変数 `vars` に関して `exprs` の偏導関数を計算します。各行に特定の式の偏導関数が含まれる `Matrix` を返します。
