```
MultinomialClassifier
```

多項分類器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
MultinomialClassifier = @load MultinomialClassifier pkg=MLJLinearModels
```

`model = MultinomialClassifier()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。

このモデルは[`LogisticClassifier`](@ref)と一致しますが、特定の最適化が特別なバイナリケースでは適用されません。ハイパーパラメータは同一です。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列が`Continuous`スカイタイプを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`<:OrderedFactor`または`<:Multiclass`である任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `lambda::Real`: `penalty`が`:l2`または`:l1`の場合の正則化項の強さ。`penalty`が`:en`の場合のL2正則化項の強さ。デフォルト: eps()
  * `gamma::Real`: `penalty`が`:en`の場合のL1正則化項の強さ。デフォルト: 0.0
  * `penalty::Union{String, Symbol}`: 使用するペナルティ、`:l2`、`:l1`、`:en`（弾性ネット）または`:none`のいずれか。デフォルト: :l2
  * `fit_intercept::Bool`: 切片をフィットさせるかどうか。デフォルト: true
  * `penalize_intercept::Bool`: 切片にペナルティを課すかどうか。デフォルト: false
  * `scale_penalty_with_samples::Bool`: サンプル数に応じてペナルティをスケーリングするかどうか。デフォルト: true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`: `MLJLinearModels.S`のインスタンスで、`S`は次のいずれか: `LBFGS`、`NewtonCG`、`ProxGrad`ですが、以下の制限が適用されます：

      * `penalty = :l2`の場合、`ProxGrad`は許可されません。それ以外の場合、`ProxGrad`が唯一の選択肢です。
      * `scitype(y) <: Finite{2}`（バイナリターゲット）でない限り、`Newton`は許可されません。

    `solver = nothing`（デフォルト）の場合、`gamma = 0`でない限り`ProxGrad(accel=true)`（FISTA）が使用され、`gamma = 0`の場合は`LBFGS()`が使用されます。

    ソルバーのエイリアス: `FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`、`ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)` デフォルト: nothing

## 例

```
using MLJ
X, y = make_blobs(centers = 3)
mach = fit!(machine(MultinomialClassifier(), X, y))
predict(mach, X)
fitted_params(mach)
```

さらに[`LogisticClassifier`](@ref)も参照してください。
