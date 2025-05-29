```
BalancedBaggingClassifier
```

バランスの取れたバギング分類器を構築するためのモデルタイプで、[MLJBalancing.jl](https://github.com/JuliaAI/MLJBalancing)に基づいています。

MLJからは、次のようにしてタイプをインポートできます。

`BalancedBaggingClassifier = @load BalancedBaggingClassifier pkg=MLJBalancing`

デフォルトのハイパーパラメータを使用してインスタンスを構築するには、構文 `bagging_model = BalancedBaggingClassifier(model=...)` を使用します。

確率的分類器である`BalancedBaggingClassifier`は、各バグの中で多数派データのみをアンダーサンプリングすることによってバギングを行い、少数派データと同じだけのサンプルを含むようにします。これは、出力スコアが平均化されるAdaboost分類器と共に提案されています。論文 Xu-Ying Liu, Jianxin Wu, & Zhi-Hua Zhou. (2009). Exploratory Undersampling for Class-Imbalance Learning. IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), 39 (2), 539–5501

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで

  * `X`: ラップされている`model`がサポートする形式の入力特徴（通常はテーブル、例：`DataFrame`、`Continuous`列がサポートされる必要があります）
  * `y`: バイナリターゲットで、`length(unique(y)) == 2`を満たす任意の`AbstractVector`である必要があります

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `model::Probabilistic`: 各バグでトレーニングに使用する分類器。
  * `T::Integer=0`: アンサンブルで使用されるバグの数。指定されていない場合は、多数派と少数派クラスの頻度の比率として設定されます。後で`report(mach)`で確認できます。
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: `AbstractRNG`オブジェクトまたは、Julia `VERSION>=1.7`の場合に`Xoshiro`で使用される`Integer`シード。そうでない場合はMersenneTwisterを使用します。

# 操作

  * `predict(mach, Xnew)`: 上記の特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。予測は確率的ですが、キャリブレーションされていません。

  * `predict_mode(mach, Xnew)`: 上記の各予測のモードを返します。

# 例

```julia
using MLJ
using Imbalance

# 基本分類器とBalancedBaggingClassifierをロード
BalancedBaggingClassifier = @load BalancedBaggingClassifier pkg=MLJBalancing
LogisticClassifier = @load LogisticClassifier pkg=MLJLinearModels verbosity=0

# 基本分類器を構築し、それを使用してBalancedBaggingClassifierを構築
logistic_model = LogisticClassifier()
model = BalancedBaggingClassifier(model=logistic_model, T=5)

# データをロードし、BalancedBaggingClassifierをトレーニング
X, y = Imbalance.generate_imbalanced_data(100, 5; num_vals_per_category = [3, 2],
                                            class_probs = [0.9, 0.1],
                                            type = "ColTable",
                                            rng=42)
julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇ 16 (19.0%)
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 84 (100.0%)

mach = machine(model, X, y) |> fit!

# トレーニングされたモデルを使用して予測

yhat = predict(mach, X)     # 確率的予測
predict_mode(mach, X)       # ポイント予測
```
