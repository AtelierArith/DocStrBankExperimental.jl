```
par2θ(θ, model)
```

パラメータ構造体をベクトルに変換する関数

  * `θ`: パラメータ構造体
  * `model`: モデル仕様 CountModel, INGARCHModel, ...

# 例

```julia-repl
model = CountModel(past_obs = 1) # INARCH(1)を指定
pars = θ2par([10, 0.5], model)
θ = par2θ(pars, model)
```
