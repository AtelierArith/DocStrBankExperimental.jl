```
MultinomialNBClassifier
```

多項ナイーブベイズ分類器を構築するためのモデルタイプで、[NaiveBayes.jl](https://github.com/dfdx/NaiveBayes.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
MultinomialNBClassifier = @load MultinomialNBClassifier pkg=NaiveBayes
```

`model = MultinomialNBClassifier()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`MultinomialNBClassifier(alpha=...)`のようにキーワード引数を提供します。

[multinomial naive Bayes classifier](https://en.wikipedia.org/wiki/Naive_Bayes_classifier#Multinomial_naive_Bayes)は、入力特徴がカウント（scitype `Count`）で構成され、固定されたターゲットクラスの観測が固定確率ベクトルを持つ多項分布から生成される場合にしばしば適用されますが、サンプルの長さは観測ごとに異なります。たとえば、特徴は感情によって分類されるテキストドキュメント内の単語のカウントを表すかもしれません。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、scitype `Count`の列を持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypeは`schema(X)`で確認できます。
  * `y`は、要素のscitypeが`Finite`である任意の`AbstractVector`です。scitypeは`schema(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `alpha=1`: トレーニングヒストグラムからの多項確率ベクトルの推定におけるリンドストーン平滑化（デフォルトはラプラス平滑化に対応）。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`に対するターゲットの予測を返します。`X`と同じscitypeである必要があります。
  * `predict_mode(mach, Xnew)`: 上記の予測のモードを返します。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `c_counts`: 各入力クラスの観測されたカウントを含む辞書。
  * `x_counts`: 各入力クラスのカテゴリカルカウントを含む辞書。
  * `x_totals`: 各カウント（入力特徴）の合計、グループ化されていない。
  * `n_obs`: トレーニングデータ内の観測の総数。

# 例

```
using MLJ
import TextAnalysis

CountTransformer = @load CountTransformer pkg=MLJText
MultinomialNBClassifier = @load MultinomialNBClassifier pkg=NaiveBayes

tokenized_docs = TextAnalysis.tokenize.([
    "I am very mad. You never listen.",
    "You seem to be having trouble? Can I help you?",
    "Our boss is mad at me. I hope he dies.",
    "His boss wants to help me. She is nice.",
    "Thank you for your help. It is nice working with you.",
    "Never do that again! I am so mad. ",
])

sentiment = [
    "negative",
    "positive",
    "negative",
    "positive",
    "positive",
    "negative",
]

mach1 = machine(CountTransformer(), tokenized_docs) |> fit!

# カウントの行列:
X = transform(mach1, tokenized_docs)

# scitype(y) <: AbstractVector{<:OrderedFactor}を確保するために:
y = coerce(sentiment, OrderedFactor)

classifier = MultinomialNBClassifier()
mach2 = machine(classifier, X, y)
fit!(mach2, rows=1:4)

# 確率的予測:
y_prob = predict(mach2, rows=5:6) # 分布
pdf.(y_prob, "positive") # "positive"の確率
log_loss(y_prob, y[5:6])

# ポイント予測:
yhat = mode.(y_prob) # または`predict_mode(mach2, rows=5:6)`
```

[`GaussianNBClassifier`](@ref)も参照してください。
