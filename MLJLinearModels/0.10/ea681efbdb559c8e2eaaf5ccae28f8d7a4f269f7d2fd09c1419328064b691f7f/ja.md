```
LADRegressor
```

LAD回帰器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
LADRegressor = @load LADRegressor pkg=MLJLinearModels
```

デフォルトのハイパーパラメータでインスタンスを構築するには、`model = LADRegressor()`を実行します。

最小絶対偏差回帰は、目的関数が次の線形モデルです。

$$
∑ρ(Xθ - y) + n⋅λ|θ|₂² + n⋅γ|θ|₁
$$

ここで、$ρ$は絶対損失で、$n$は観測数です。

`scale_penalty_with_samples = false`の場合、目的関数は次のようになります。

$$
∑ρ(Xθ - y) + λ|θ|₂² + γ|θ|₁
$$

。

"ハイパーパラメータ"の下に示されているように、さまざまなソルバーオプションがあります。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列が`Continuous`スカイタイプを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`Continuous`である任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

`RobustRegressor`も参照してください。

## パラメータ

  * `lambda::Real`: `penalty`が`:l2`または`:l1`の場合の正則化項の強さ。`penalty`が`:en`の場合のL2正則化項の強さ。デフォルト：1.0
  * `gamma::Real`: `penalty`が`:en`の場合のL1正則化項の強さ。デフォルト：0.0
  * `penalty::Union{String, Symbol}`: 使用するペナルティ、`:l2`、`:l1`、`:en`（エラスティックネット）または`:none`のいずれか。デフォルト：:l2
  * `fit_intercept::Bool`: 切片をフィットさせるかどうか。デフォルト：true
  * `penalize_intercept::Bool`: 切片にペナルティを課すかどうか。デフォルト：false
  * `scale_penalty_with_samples::Bool`: 観測数でペナルティをスケーリングするかどうか。デフォルト：true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: `MLJLinearModels.S`のインスタンスで、`S`は次のいずれか：`LBFGS`、`IWLSCG`（`penalty = :l2`の場合）、それ以外は`ProxGrad`。

    `solver = nothing`（デフォルト）の場合、`penalty = :l2`の場合は`LBFGS()`が使用され、それ以外の場合は`ProxGrad(accel=true)`（FISTA）が使用されます。

    ソルバーのエイリアス：`FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`、`ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)` デフォルト：nothing

## 例

```
using MLJ
X, y = make_regression()
mach = fit!(machine(LADRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```
