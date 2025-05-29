```
LinearRegressor
```

線形回帰器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
LinearRegressor = @load LinearRegressor pkg=MLJLinearModels
```

デフォルトのハイパーパラメータでインスタンスを構築するには、`model = LinearRegressor()`を実行します。

このモデルは、目的関数

$$
|Xθ - y|₂²/2
$$

を持つ標準的な線形回帰を提供します。

異なるソルバーオプションが存在し、以下の「ハイパーパラメータ」で示されています。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列が`Continuous`スカイタイプを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`Continuous`である任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `fit_intercept::Bool`: 切片をフィットさせるかどうか。デフォルト：true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: "任意の`MLJLinearModels.Analytical`のインスタンス。Cholesky用には`Analytical()`を、共役勾配法用には`CG()=Analytical(iterative=true)`を使用します。

    `solver = nothing`（デフォルト）の場合、`Analytical()`が使用されます。デフォルト：nothing

## 例

```
using MLJ
X, y = make_regression()
mach = fit!(machine(LinearRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```
