```
var(model, θ, ofλ = false)
```

INGARCH(p, q)プロセスの周辺分散。回帰子や対数リンクを持つモデルは対象外です。

  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたはパラメータ型）
  * `ofλ`: trueの場合、条件付き平均列の周辺平均が返されます

# 例

```julia-repl
model = Model(pastObs = 1)
var(model, [10, 0.5])
```
