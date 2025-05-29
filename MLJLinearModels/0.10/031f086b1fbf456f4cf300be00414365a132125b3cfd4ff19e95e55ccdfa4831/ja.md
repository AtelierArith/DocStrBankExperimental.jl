```
LogisticClassifier
```

ロジスティック分類器を構築するためのモデルタイプで、[MLJLinearModels.jl](https://github.com/alan-turing-institute/MLJLinearModels.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
LogisticClassifier = @load LogisticClassifier pkg=MLJLinearModels
```

`model = LogisticClassifier()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。

このモデルは「ロジスティック回帰」として一般的に知られています。これは、バイナリおよびマルチクラス分類のための標準的な分類器です。目的関数は、ロジスティック損失（バイナリターゲット）または多項（ソフトマックス）損失を適用し、混合L1/L2ペナルティを持ちます：

$$
L(y, Xθ) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁
$$

。

ここで$L$は`MLJLinearModels.LogisticLoss`または`MLJLinearModels.MultiClassLoss`のいずれかで、$λ$と$γ$はL2（それぞれL1）正則化成分の強さを示し、$n$はトレーニング観測の数です。

`scale_penalty_with_samples = false`の場合、目的関数は次のようになります。

$$
L(y, Xθ) + λ|θ|₂²/2 + γ|θ|₁
$$

。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列が`Continuous`スカイタイプを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`<:OrderedFactor`または`<:Multiclass`である任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `lambda::Real`：`penalty`が`:l2`または`:l1`の場合の正則化項の強さ、`penalty`が`:en`の場合のL2正則化項の強さ。デフォルト：eps()
  * `gamma::Real`：`penalty`が`:en`の場合のL1正則化項の強さ。デフォルト：0.0
  * `penalty::Union{String, Symbol}`：使用するペナルティ、`:l2`、`:l1`、`:en`（エラスティックネット）または`:none`のいずれか。デフォルト：:l2
  * `fit_intercept::Bool`：切片をフィットさせるかどうか。デフォルト：true
  * `penalize_intercept::Bool`：切片にペナルティを課すかどうか。デフォルト：false
  * `scale_penalty_with_samples::Bool`：サンプル数でペナルティをスケールするかどうか。デフォルト：true
  * `solver::Union{Nothing, MLJLinearModels.Solver}`：`MLJLinearModels.S`のインスタンスで、`S`は次のいずれか：`LBFGS`、`Newton`、`NewtonCG`、`ProxGrad`ですが、次の制限が適用されます：

      * `penalty = :l2`の場合、`ProxGrad`は許可されません。それ以外の場合、`ProxGrad`が唯一の選択肢です。
      * `scitype(y) <: Finite{2}`（バイナリターゲット）でない限り、`Newton`は許可されません。

    `solver = nothing`（デフォルト）の場合、`gamma = 0`でない限り`ProxGrad(accel=true)`（FISTA）が使用され、`gamma = 0`の場合は`LBFGS()`が使用されます。

    ソルバーのエイリアス：`FISTA(; kwargs...) = ProxGrad(accel=true, kwargs...)`、`ISTA(; kwargs...) = ProxGrad(accel=false, kwargs...)` デフォルト：nothing

## 例

```
using MLJ
X, y = make_blobs(centers = 2)
mach = fit!(machine(LogisticClassifier(), X, y))
predict(mach, X)
fitted_params(mach)
```

他に[`MultinomialClassifier`](@ref)も参照してください。
