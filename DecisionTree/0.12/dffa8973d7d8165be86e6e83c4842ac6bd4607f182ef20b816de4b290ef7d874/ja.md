```
RandomForestClassifier(; n_subfeatures::Int=-1,
                       n_trees::Int=10,
                       partial_sampling::Float=0.7,
                       max_depth::Int=-1,
                       rng=Random.GLOBAL_RNG,
                       impurity_importance::Bool=true)
```

ランダムフォレスト分類。詳細は [DecisionTree.jlのドキュメント](https://github.com/bensadeghi/DecisionTree.jl) を参照してください。

ハイパーパラメータ:

  * `n_subfeatures`: スプリットごとにランダムに考慮する特徴の数 (デフォルト: -1, sqrt(# 特徴))
  * `n_trees`: 訓練する木の数 (デフォルト: 10)
  * `partial_sampling`: 各木を訓練するためのサンプルの割合 (デフォルト: 0.7)
  * `max_depth`: 決定木の最大深さ (デフォルト: 制限なし)
  * `min_samples_leaf`: 各葉が持つ必要のある最小サンプル数
  * `min_samples_split`: スプリットに必要な最小サンプル数
  * `min_purity_increase`: スプリットに必要な最小純度
  * `rng`: 使用する乱数生成器。`Int`を指定すると、新しい乱数生成器のシードとして使用されます。マルチスレッドのフォレストは`Int`でシードを設定する必要があります。
  * `impurity_importance`: `Mean Decrease in Impurity (MDI)`を使用して特徴の重要度を計算するかどうか。詳細は [`DecisionTree.impurity_importance`](@ref) を参照してください。

`fit!`、`predict`、`predict_proba`、`get_classes` を実装しています。
