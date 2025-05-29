```
LassoRegressor
```

Lasso回帰器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
LassoRegressor = @load LassoRegressor pkg=MLJLinearModels
```

`model = LassoRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。

Lasso回帰は、目的関数が次の線形モデルです。

$$
|Xθ - y|₂²/2 + n⋅λ|θ|₁
$$

ここで、$n$は観測の数です。

`scale_penalty_with_samples = false`の場合、目的関数は次のようになります。

$$
|Xθ - y|₂²/2 + λ|θ|₁
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

  * `lambda::Real`: L1正則化の強さ。デフォルト：1.0
  * `fit_intercept::Bool`: 切片をフィットさせるかどうか。デフォルト：true
  * `penalize_intercept::Bool`: 切片にペナルティを課すかどうか。デフォルト：false
  * `scale_penalty_with_samples::Bool`: 観測数でペナルティをスケーリングするかどうか。デフォルト：true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: `MLJLinearModels.ProxGrad`の任意のインスタンス。`solver=nothing`（デフォルト）の場合、`ProxGrad(accel=true)`（FISTA）が使用されます。ソルバーのエイリアス：`FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`、`ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)`。デフォルト：nothing

## 例

```
using MLJ
X, y = make_regression()
mach = fit!(machine(LassoRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```

[`ElasticNetRegressor`](@ref)も参照してください。
