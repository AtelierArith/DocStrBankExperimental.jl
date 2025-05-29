```
mean(model, θ, ofλ = false)
```

INGARCH(p, q)プロセスの周辺平均。回帰子や対数リンクを持つモデルはカバーされていません。

  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたはパラメータ型）
  * `ofλ`: trueの場合、条件付き平均列の周辺平均が返されます

# 例

```julia-repl
model = Model(pastObs = 1)
mean(model, [10, 0.5])
```
