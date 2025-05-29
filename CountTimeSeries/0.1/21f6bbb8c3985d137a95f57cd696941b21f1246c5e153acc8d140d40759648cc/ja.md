```
mean(model, θ)
```

INARMA(p, q)プロセスの周辺平均。回帰子を含むモデルはカバーされていません。

  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたはパラメータ型）

# 例

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
mean(model, [10, 0.5])
```
