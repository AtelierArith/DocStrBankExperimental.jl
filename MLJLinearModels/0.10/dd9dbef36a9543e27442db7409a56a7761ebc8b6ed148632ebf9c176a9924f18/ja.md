```
ElasticNetRegressor
```

弾性ネット回帰器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
ElasticNetRegressor = @load ElasticNetRegressor pkg=MLJLinearModels
```

デフォルトのハイパーパラメータでインスタンスを構築するには、`model = ElasticNetRegressor()`を実行します。

弾性ネットは、目的関数が次のような線形モデルです。

$$
|Xθ - y|₂²/2 + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁
$$

ここで、$n$は観測の数です。

`scale_penalty_with_samples = false`の場合、目的関数は次のようになります。

$$
|Xθ - y|₂²/2 + λ|θ|₂²/2 + γ|θ|₁
$$

。

"ハイパーパラメータ"の下に示されているように、さまざまなソルバーオプションがあります。

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

  * `lambda::Real`: L2正則化の強さ。デフォルト: 1.0
  * `gamma::Real`: L1正則化の強さ。デフォルト: 0.0
  * `fit_intercept::Bool`: 切片をフィットさせるかどうか。デフォルト: true
  * `penalize_intercept::Bool`: 切片にペナルティを課すかどうか。デフォルト: false
  * `scale_penalty_with_samples::Bool`: 観測の数でペナルティをスケールするかどうか。デフォルト: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: `MLJLinearModels.ProxGrad`の任意のインスタンス。

    `solver=nothing`（デフォルト）の場合、`ProxGrad(accel=true)`（FISTA）が使用されます。

    ソルバーのエイリアス: `FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`、`ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)`。デフォルト: nothing

## 例

```
using MLJ
X, y = make_regression()
mach = fit!(machine(ElasticNetRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```

また、[`LassoRegressor`](@ref)も参照してください。
