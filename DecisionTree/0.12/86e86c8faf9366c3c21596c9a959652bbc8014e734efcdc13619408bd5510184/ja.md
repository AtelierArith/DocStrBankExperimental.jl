```
DecisionTreeRegressor(; pruning_purity_threshold=0.0,
                      max_depth::Int-1,
                      min_samples_leaf::Int=5,
                      min_samples_split::Int=2,
                      min_purity_increase::Float=0.0,
                      n_subfeatures::Int=0,
                      rng=Random.GLOBAL_RNG,
                      impurity_importance::Bool=true)
```

決定木回帰。詳細は[DecisionTree.jlのドキュメント](https://github.com/bensadeghi/DecisionTree.jl)を参照してください。

ハイパーパラメータ:

  * `pruning_purity_threshold`: (後処理剪定) `>=thresh` の結合純度を持つ葉をマージします（デフォルト: 剪定なし）。この精度ベースの方法は回帰木には適さない場合があります。
  * `max_depth`: 決定木の最大深さ（デフォルト: 最大なし）
  * `min_samples_leaf`: 各葉が持つ必要がある最小サンプル数（デフォルト: 5）
  * `min_samples_split`: 分割に必要な最小サンプル数（デフォルト: 2）
  * `min_purity_increase`: 分割に必要な最小純度（デフォルト: 0.0）
  * `n_subfeatures`: ランダムに選択する特徴の数（デフォルト: すべて保持）
  * `rng`: 使用する乱数生成器。`Int`を指定すると、新しい乱数生成器のシードとして使用されます。
  * `impurity_importance`: `Mean Decrease in Impurity (MDI)`を使用して特徴の重要度を計算するかどうか。詳細は[`DecisionTree.impurity_importance`](@ref)を参照してください。

`fit!`、`predict`、`get_classes`を実装します。
