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

Calculate feature importance by shuffling each feature.

  * `trees`: a `DecisionTree.Leaf` object, `DecisionTree.Node` object, `DecisionTree.Root` object, `DecisionTree.Ensemble` object or `Tuple{DecisionTree.Ensemble, AbstractVector}` object (for adaboost model)
  * `score`: a function for evaluating model performance with the form of `score(model, y, X)`

# Return a `NamedTuple`

  * Fields

1. `mean`: mean of feature importance of each shuffle
2. `std`: standard deviation of feature importance of each shuffle
3. `scores`: scores of each shuffle

For algorithm details, please see [Permutation feature importanc](https://scikit-learn.org/stable/modules/permutation_importance.html).
