```
θ2par(θ, model)
```

パラメータベクトルを構造体に変換する関数

  * `θ`: パラメータベクトル
  * `model`: モデル仕様 CountModel, INGARCHModel, INARMAModel, ...

パラメータベクトルは適切な長さである必要があります。

# 例

```julia-repl
model = Model(pastObs = 1) # INARCH(1)を指定
θ2par([10, 0.5], model)
```
