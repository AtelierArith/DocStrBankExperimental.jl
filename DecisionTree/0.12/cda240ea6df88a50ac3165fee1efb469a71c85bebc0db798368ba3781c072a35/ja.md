```
build_forest(labels, features, options...; keyword_options...)
```

指定された `labels` (ターゲット) と `features` (パターン) を使用して、標準の CART 決定木に基づいて構築されたランダムフォレストモデルをトレーニングします。ここで：

  * `labels` は任意の `AbstractVector` です。要素の型が `AbstractFloat` の場合は回帰が適用され、それ以外の場合は分類が適用されます。
  * `features` は任意の `AbstractMatrix{T}` で、`T` は `<` での順序付けをサポートしている必要があります (順序付けされていないカテゴリカル特徴はサポートされていません)。行列はサイズ `(n, p)` でなければならず、ここで `n = length(labels)` (観測値としての行) です。

エントロピー損失はノードの分割を決定するために使用されます。つまり、個々の木は `loss=DecisionTree.util.entropy` オプションを使用して `build_tree` を呼び出すことでトレーニングされます。

新しい特徴に対して予測を行うには [`apply_forest`](@ref) と [`apply_forest_proba`](@ref) を使用します。以下の例を参照してください。

# ハイパーパラメータ

これらは `options` と `keyword_options` として指定されます：

## オプション

  * `n_subfeatures=-1`: 分割ごとにランダムに考慮する特徴の数。 `-1` に等しい場合、特徴の数 `p` の平方根が使用されます。
  * `n_trees=10`: トレーニングする木の数。
  * `partial_sampling=0.7`: 各木をトレーニングするためのサンプルの割合。
  * `max_depth=-1`: 決定木の最大深さ。 `-1` に等しい場合は制限なし。
  * `min_samples_leaf`: 各葉が持つ必要がある最小サンプル数。回帰の場合のデフォルトは `5`、分類の場合は `1` です。
  * `min_samples_split=2`: 分割に必要な最小サンプル数。
  * `min_purity_increase=0`: 分割をトリガーするために必要な最小純度。

## キーワードオプション

  * `rng=Random.GLOBAL_RNG`: 使用する乱数生成器またはシード (整数)。 `Random.seed!` をサポートする任意の `AbstractRNG` オブジェクトを使用できます。各木は独自の生成器を持ちます。
  * `impurity_importance=true`: 不純物特徴の重要性を計算するかどうか。

# 例

```
features, labels = load_data("iris")    # "adult" および "digits" データセットも参照してください
```

読み込まれたデータは `Array{Any}` 型であるため、パフォーマンスを向上させるために具体的な型にキャストします：

```
features = float.(features)
labels = string.(labels)
```

2つのランダムな特徴、10本の木、各木ごとのサンプルの0.5の割合、最大木の深さ6を使用してランダムフォレスト分類器をトレーニングします：

```
model = build_forest(labels, features, 2, 10, 0.5, 6)
```

新しいデータに対して予測を取得します：

```
new_features = [5.9 3.0 5.1 1.9
                1.0 2.0 3.9 2.0]
apply_forest(model, new_features)
```

確率的予測を取得します：

```
apply_forest_proba(
    model,
    new_features,
    ["Iris-setosa", "Iris-versicolor", "Iris-virginica"],
)
```

不純物特徴の重要性を取得します：

```
impurity_importance(model)
```

分割ごとに2つのランダムな特徴を使用して、3分割交差検証を実行します：

```
n_folds=3
n_subfeatures=2
accuracy = nfoldCV_forest(labels, features, n_folds, n_subfeatures)
```

[`build_tree`](@ref)、[`apply_forest`](@ref)、[`apply_forest_proba`](@ref)、[`impurity_importance`](@ref)、[`split_importance`](@ref)、[`permutation_importance`](@ref)、[`nfoldCV_forest`](@ref) も参照してください。
