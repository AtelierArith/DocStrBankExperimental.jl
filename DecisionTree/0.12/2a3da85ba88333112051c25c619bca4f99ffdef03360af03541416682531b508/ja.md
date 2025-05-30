```
permutation_importance(
    trees   :: DecisionTreeEstimator, 
    X       :: AbstractMatrix,
    y       :: AbstractVector; 
    score   :: Function,
    n_iter  :: Int = 3,
    rng     =  Random.GLOBAL_RNG
    )
```

各特徴量をシャッフルすることで特徴量の重要性を計算します。

引数と出力は、一般的な `DecisionTree` のオブジェクトに対する `permutation_importance` と似ていますが、`score` は `score(model, X, y)` の形式を取り、デフォルトの関数は `score_fn` によって決定されます。`DecisionTreeClassifier`、`RandomForestClassifier`、および `AdaBoostStumpClassifier` のデフォルトは `accuracy` であり、`DecisionTreeRegressor` および `RandomForestRegressor` の場合は `R2` です。
