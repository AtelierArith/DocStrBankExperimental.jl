```
isconverged(new::Float64, old::Float64, tol::Float64, ε::Float64, increasing::Bool)
```

`new`が`old`に十分近いかどうかを確認します。

# 引数

  * `new`: 新しい目的関数または損失
  * `old`: 古い目的関数または損失
  * `tol`: 許容誤差
  * `ε`: 小さなFloat64
  * `increasing`: `new`が各イテレーションで`old`に対して増加する場合はtrue
