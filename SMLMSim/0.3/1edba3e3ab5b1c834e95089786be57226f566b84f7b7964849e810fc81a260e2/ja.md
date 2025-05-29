```
simulate(sim::AbstractSim; kwargs...)
```

すべてのシミュレーションタイプのための汎用インターフェース。具体的なシミュレーションタイプに基づいて適切なメソッドにディスパッチします。

# 引数

  * `sim::AbstractSim`: シミュレーション設定オブジェクト
  * `kwargs...`: シミュレーションタイプに特有の追加キーワード引数

# 戻り値

  * 特定のシミュレーションメソッドの結果

# 例

```julia
# 静的SMLMシミュレーション設定を作成
params = StaticSMLMParams(
    density = 1.0,        # ρからdensityに変更
    σ_psf = 0.13
)

# シミュレーションを実行
results = simulate(params)
```
