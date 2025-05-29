```
limit(expr, var, h[, side::Symbol])
```

`expr`の`var`が`h`に近づくときのリミットを計算し、`(limit, assumptions)`を返します。すべての`assumptions`が真であれば、返される`limit`は正しいです。

`side`は`var`が`h`に近づく方向を示します。`side`は`:left`、`:right`、または`:both`のいずれかである必要があります。`side`が`:both`で、両側が一致しない場合はエラーがスローされます。`side`は有限の`h`の場合は`:both`、`h = Inf`の場合は`:left`、`h = -Inf`の場合は`:right`にデフォルト設定されています。
