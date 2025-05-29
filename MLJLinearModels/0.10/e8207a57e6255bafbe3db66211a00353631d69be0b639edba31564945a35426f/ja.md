```
HuberRegressor
```

ハイパーレグレッサーを構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
HuberRegressor = @load HuberRegressor pkg=MLJLinearModels
```

`model = HuberRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。

このモデルは[`RobustRegressor`](@ref)と一致しますが、ロバスト損失`rho`は`HuberRho(delta)`に固定されており、ここで`delta`は新しいハイパーパラメータです。

異なるソルバーオプションが存在し、以下の「ハイパーパラメータ」に示されています。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、`Continuous`スカイタイプを持つ列を持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`Continuous`である任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `delta::Real`: `HuberRho`関数をパラメータ化します（損失が二次損失であるボールの半径）。デフォルト: 0.5
  * `lambda::Real`: `penalty`が`:l2`または`:l1`の場合の正則化項の強さ。`penalty`が`:en`の場合のL2正則化項の強さ。デフォルト: 1.0
  * `gamma::Real`: `penalty`が`:en`の場合のL1正則化項の強さ。デフォルト: 0.0
  * `penalty::Union{String, Symbol}`: 使用するペナルティ、`:l2`、`:l1`、`:en`（弾性ネット）または`:none`のいずれか。デフォルト: :l2
  * `fit_intercept::Bool`: 切片をフィットさせるかどうか。デフォルト: true
  * `penalize_intercept::Bool`: 切片にペナルティを課すかどうか。デフォルト: false
  * `scale_penalty_with_samples::Bool`: 観測数に応じてペナルティをスケールするかどうか。デフォルト: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: `MLJLinearModels.S`のインスタンスで、`S`は`LBFGS`、`IWLSCG`、`Newton`、`NewtonCG`のいずれかで、`penalty = :l2`の場合、そうでなければ`ProxGrad`です。

    `solver = nothing`（デフォルト）の場合、`penalty = :l2`の場合は`LBFGS()`が使用され、それ以外の場合は`ProxGrad(accel=true)`（FISTA）が使用されます。

    ソルバーのエイリアス: `FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`、`ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)` デフォルト: nothing

## 例

```
using MLJ
X, y = make_regression()
mach = fit!(machine(HuberRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```

さらに[`RobustRegressor`](@ref)、[`QuantileRegressor`](@ref)も参照してください。
