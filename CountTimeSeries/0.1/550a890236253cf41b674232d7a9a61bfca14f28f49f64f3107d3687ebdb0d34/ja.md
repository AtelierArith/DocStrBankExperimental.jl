```
simulate(T, model, θ; burnin, pinfirst)
```

カウントデータモデルから時系列を生成する関数。

  * `T`: 時系列の長さ
  * `model`: モデル仕様
  * `θ`: パラメータ（ベクトルまたは構造体）
  * `burnin`: バーンイン観測の数、デフォルトは500
  * `pinfirst`: 最初の観測値を設定する（バーンインの代わりに）

# 例

```julia-repl
model = CountModel(pastObs = 1)
simulate(100, model, [10, 0.5])
```
