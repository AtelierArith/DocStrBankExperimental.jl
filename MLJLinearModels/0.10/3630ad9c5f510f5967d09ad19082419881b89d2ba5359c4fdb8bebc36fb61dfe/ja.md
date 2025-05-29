```
RidgeRegressor
```

リッジ回帰器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
RidgeRegressor = @load RidgeRegressor pkg=MLJLinearModels
```

`model = RidgeRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。

リッジ回帰は、目的関数が次のような線形モデルです。

$$
|Xθ - y|₂²/2 + n⋅λ|θ|₂²/2
$$

ここで、$n$は観測の数です。

`scale_penalty_with_samples = false`の場合、目的関数は次のようになります。

$$
|Xθ - y|₂²/2 + λ|θ|₂²/2
$$

。

異なるソルバーオプションが存在し、以下の「ハイパーパラメータ」の下に示されています。

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

  * `lambda::Real`: L2正則化の強さ。デフォルト: 1.0
  * `fit_intercept::Bool`: 切片をフィットさせるかどうか。デフォルト: true
  * `penalize_intercept::Bool`: 切片にペナルティを課すかどうか。デフォルト: false
  * `scale_penalty_with_samples::Bool`: 観測の数でペナルティをスケーリングするかどうか。デフォルト: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: `MLJLinearModels.Analytical`の任意のインスタンス。Cholesky用には`Analytical()`を、共役勾配用には`CG()=Analytical(iterative=true)`を使用します。`solver = nothing`（デフォルト）の場合は`Analytical()`が使用されます。デフォルト: nothing

## 例

```
using MLJ
X, y = make_regression()
mach = fit!(machine(RidgeRegressor(), X, y))
predict(mach, X)
fitted_params(mach)
```

他に[`ElasticNetRegressor`](@ref)も参照してください。
