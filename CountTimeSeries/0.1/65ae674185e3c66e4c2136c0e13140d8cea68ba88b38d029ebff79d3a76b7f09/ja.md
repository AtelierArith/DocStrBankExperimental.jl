```
var(model, θ)
```

INARMA(p, q)プロセスの周辺分散。回帰子を含むモデルは対象外です。

  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたはパラメータ型）

# 例

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
var(model, [10, 0.5])
```
