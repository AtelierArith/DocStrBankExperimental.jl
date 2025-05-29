```
BalancedModel(; model=nothing, balancer1=balancer_model1, balancer2=balancer_model2, ...)
BalancedModel(model;  balancer1=balancer_model1, balancer2=balancer_model2, ...)
```

与えられた分類モデルと、すべてが `MLJModelInterface` を実装する1つ以上のバランサーモデルに対して、`BalancedModel` は任意の数のバランシングモデルと分類器を一緒にシーケンシャルパイプラインでラップすることを可能にします。

# 操作

  * トレーニング中、データは最初に `balancer1` に渡され、その結果が `balancer2` に渡され、次にその結果が最終バランサーに渡され、最終的なバランサーの結果が分類器に渡されてトレーニングされます。
  * 予測中、バランサーは影響を与えません。

# 引数

  * `model::Supervised`: `MLJModelInterface` を実装する分類モデル。
  * `balancer1::Static=...`: データを渡す最初のバランサーモデル。このキーワード引数は任意の名前を持つことができます。
  * `balancer2::Static=...`: データを渡す2番目のバランサーモデル。このキーワード引数は任意の名前を持つことができます。
  * そして、任意の数のバランサーのために続きます。

# 戻り値

  * モデルの予測タイプに応じて、ProbabilisticBalancedModel または DeterministicBalancedModel のインスタンス。

# 例

```julia
using MLJ
using Imbalance

# データを生成
X, y = Imbalance.generate_imbalanced_data(1000, 5; class_probs=[0.2, 0.3, 0.5])

# 分類およびバランシングモデルを準備
SMOTENC = @load SMOTENC pkg=Imbalance verbosity=0
TomekUndersampler = @load TomekUndersampler pkg=Imbalance verbosity=0
LogisticClassifier = @load LogisticClassifier pkg=MLJLinearModels verbosity=0

oversampler = SMOTENC(k=5, ratios=1.0, rng=42)
undersampler = TomekUndersampler(min_ratios=0.5, rng=42)
logistic_model = LogisticClassifier()

# それらを BalancedModel にラップ
balanced_model = BalancedModel(model=logistic_model, balancer1=oversampler, balancer2=undersampler)

# これで、トレーニング、検証、ファインチューニングなどができる統一モデルとして機能します。
mach = machine(balanced_model, X, y)
fit!(mach)
```
