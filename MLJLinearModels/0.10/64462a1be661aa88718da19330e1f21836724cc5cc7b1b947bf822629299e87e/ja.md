```
RobustRegressor
```

ロバスト回帰器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
RobustRegressor = @load RobustRegressor pkg=MLJLinearModels
```

`model = RobustRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。

ロバスト回帰は、目的関数が次のような線形モデルです。

$$
∑ρ(Xθ - y) + n⋅λ|θ|₂² + n⋅γ|θ|₁
$$

ここで、$ρ$はロバスト損失関数（例：Huber関数）で、$n$は観測数です。

`scale_penalty_with_samples = false`の場合、目的関数は次のようになります。

$$
∑ρ(Xθ - y) + λ|θ|₂² + γ|θ|₁
$$

。

異なるソルバーオプションが存在し、以下の「ハイパーパラメータ」の下に示されています。

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

  * `rho::MLJLinearModels.RobustRho`：ロバスト損失のタイプで、`MLJLinearModels.L`の任意のインスタンスである必要があります。ここで、`L`は次のいずれかです：`AndrewsRho`、`BisquareRho`、`FairRho`、`HuberRho`、`LogisticRho`、`QuantileRho`、`TalwarRho`、`HuberRho`、`TalwarRho`。デフォルト：HuberRho(0.1)
  * `lambda::Real`：`penalty`が`:l2`または`:l1`の場合の正則化の強さ。`penalty`が`:en`の場合のL2正則化の強さ。デフォルト：1.0
  * `gamma::Real`：`penalty`が`:en`の場合のL1正則化の強さ。デフォルト：0.0
  * `penalty::Union{String, Symbol}`：使用するペナルティで、`:l2`、`:l1`、`:en`（エラスティックネット）または`:none`のいずれかです。デフォルト：:l2
  * `fit_intercept::Bool`：切片をフィットさせるかどうか。デフォルト：true
  * `penalize_intercept::Bool`：切片にペナルティを課すかどうか。デフォルト：false
  * `scale_penalty_with_samples::Bool`：観測数に応じてペナルティをスケールするかどうか。デフォルト：true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`：`MLJLinearModels.S`の任意のインスタンスで、`S`は次のいずれかです：`LBFGS`、`IWLSCG`、`Newton`、`NewtonCG`（`penalty = :l2`の場合）、それ以外は`ProxGrad`です。

    `solver = nothing`（デフォルト）の場合、`penalty = :l2`の場合は`LBFGS()`が使用され、それ以外の場合は`ProxGrad(accel=true)`（FISTA）が使用されます。

    ソルバーのエイリアス：`FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`、`ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)` デフォルト：nothing

## 例

```
using MLJ
X, y = make_regression()
mach = fit!(machine(RobustRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```

他にも[`HuberRegressor`](@ref)、[`QuantileRegressor`](@ref)を参照してください。
