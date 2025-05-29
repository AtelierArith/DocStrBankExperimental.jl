```
acvf(model, θ, lagMax)
```

INARMA(p, q)プロセスの自己共分散関数。回帰子を含むモデルは対象外です。

  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたはパラメータ型）
  * `lagMax`: 計算する最大ラグ

# 例

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
acvf(model, [10, 0.5])
```
