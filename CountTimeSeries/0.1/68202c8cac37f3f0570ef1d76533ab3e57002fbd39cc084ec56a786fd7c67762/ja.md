```
acf(model, θ, lagMax)
```

INARMA(p, q)プロセスの自己相関関数。回帰子を持つモデルはカバーされていません。

  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたはパラメータ型）
  * `lagMax`: 計算する最大ラグ

# 例

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
acf(model, [10, 0.5])
```
