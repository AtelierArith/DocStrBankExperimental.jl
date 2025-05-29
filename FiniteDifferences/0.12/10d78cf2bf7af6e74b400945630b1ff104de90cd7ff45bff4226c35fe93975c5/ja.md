```
assert_approx_equal(x, y, ε_abs, ε_rel[, desc])
```

`x`が`y`に近似等しいことを確認します。

`eps_z = eps_abs / eps_rel`とします。`abs(x) < eps_z`および`abs(y) < eps_z`の場合、`x`と`y`は小さいと呼び、そうでない場合は大きいと呼びます。この関数が`True`を返す場合、`x`と`y`が大きい場合は`abs(x - y) < 2 eps_rel max(abs(x), abs(y))`が保証され、`x`と`y`が小さい場合は`abs(x - y) < 2 eps_abs`が保証されます。

# 引数

  * `x`: 比較する最初のオブジェクト。
  * `y`: 比較する2番目のオブジェクト。
  * `ε_abs`: 絶対許容誤差。
  * `ε_rel`: 相対許容誤差。
  * `desc`: 比較の説明。省略するか`false`に設定すると説明はありません。
