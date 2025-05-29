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

Calculate feature importance by shuffling each feature. 

The arguments and outputs are similar to `permutation_importance` for generic `DecisionTree`'s object, except that `score` takes the form of `score(model, X, y)` with default function determined by function `score_fn`. For `DecisionTreeClassifier`, `RandomForestClassifier` and `AdaBoostStumpClassifier`, the default is `accuracy`; for `DecisionTreeRegressor` and `RandomForestRegressor`, it is `R2`.
