```
minimize(f, (x_left, x_right); atol)
```

区間 `[x_left, x_right]` で凸関数 `f` を最小化します。

# 引数

  * f: 最小化すべき関数で、微分可能である必要はありません。
  * atol: 検索許容誤差で、`isapprox(true_minimizer, sol.minimizer, atol=atol)`

が成り立つ必要があります。
