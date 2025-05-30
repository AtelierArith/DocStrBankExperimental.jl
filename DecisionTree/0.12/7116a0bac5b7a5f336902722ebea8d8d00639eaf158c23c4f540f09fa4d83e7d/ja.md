```
permutation_importances(
                        trees   :: U,
                        labels  :: AbstractVector{T},
                        features:: AbstractVecOrMat{S},
                        score   :: Function,
                        n_iter  :: Int = 3;
                        rng     =  Random.GLOBAL_RNG
                        )
```

各特徴量をシャッフルすることで特徴量の重要性を計算します。

  * `trees`: `DecisionTree.Leaf` オブジェクト、`DecisionTree.Node` オブジェクト、`DecisionTree.Root` オブジェクト、`DecisionTree.Ensemble` オブジェクト、または `Tuple{DecisionTree.Ensemble, AbstractVector}` オブジェクト（アダブーストモデル用）
  * `score`: `score(model, y, X)` の形式でモデルのパフォーマンスを評価するための関数

# `NamedTuple` を返す

  * フィールド

1. `mean`: 各シャッフルの特徴量の重要性の平均
2. `std`: 各シャッフルの特徴量の重要性の標準偏差
3. `scores`: 各シャッフルのスコア

アルゴリズムの詳細については [Permutation feature importanc](https://scikit-learn.org/stable/modules/permutation_importance.html) を参照してください。
