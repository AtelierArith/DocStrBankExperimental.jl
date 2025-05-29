```
build_forest(labels, features, options...; keyword_options...)
```

Train a random forest model, built on standard CART decision trees, using the specified `labels` (target) and `features` (patterns). Here:

  * `labels` is any `AbstractVector`. If the element type is `AbstractFloat`, regression is applied, and otherwise classification is applied.
  * `features` is any `AbstractMatrix{T}` where `T` supports ordering with `<` (unordered categorical features are not supported). The matrix must have size `(n, p)` where `n = length(labels)` (observations as rows).

Entropy loss is used for determining node splits, i.e., individual trees are trained by calling `build_tree` with the `loss=DecisionTree.util.entropy` option.

Use [`apply_forest`](@ref) and [`apply_forest_proba`](@ref) to make predictions on new features. See the example below.

# Hyperparameters

These are specified as  `options` and `keyword_options`:

## Options

  * `n_subfeatures=-1`: number of features to consider at random per split. If equal to `-1`, then the square root of the number of features `p` is used
  * `n_trees=10`: number of trees to train
  * `partial_sampling=0.7`: fraction of samples on which to train each tree
  * `max_depth=-1`: maximum depth of the decision trees; no limit if equal to `-1`
  * `min_samples_leaf`: the minimum number of samples each leaf needs to have; default is `5` for regression and `1` for classification
  * `min_samples_split=2`: the minimum number of samples needed for a split
  * `min_purity_increase=0`: minimum purity needed to trigger a split

## Keyword options

  * `rng=Random.GLOBAL_RNG`: the random number generator or seed (integer) to use. Any `AbstractRNG` object supporting `Random.seed!` can be used; each tree gets it's own generator.
  * `impurity_importance=true`: whether to compute impurity feature importances

# Example

```
features, labels = load_data("iris")    # also see "adult" and "digits" datasets
```

The data loaded are of type `Array{Any}`, so we cast them to concrete types for better performance:

```
features = float.(features)
labels = string.(labels)
```

Training a random forest classifier using 2 random features, 10 trees, 0.5 portion of samples per tree, and a maximum tree depth of 6:

```
model = build_forest(labels, features, 2, 10, 0.5, 6)
```

Get predictions on new data:

```
new_features = [5.9 3.0 5.1 1.9
                1.0 2.0 3.9 2.0]
apply_forest(model, new_features)
```

Get probabilistic predictions:

```
apply_forest_proba(
    model,
    new_features,
    ["Iris-setosa", "Iris-versicolor", "Iris-virginica"],
)
```

Get impurity feature importances:

```
impurity_importance(model)
```

Run 3-fold cross validation for forests, using 2 random features per split:

```
n_folds=3
n_subfeatures=2
accuracy = nfoldCV_forest(labels, features, n_folds, n_subfeatures)
```

See also [`build_tree`](@ref), [`apply_forest`](@ref), [`apply_forest_proba`](@ref), [`impurity_importance`](@ref), [`split_importance`](@ref), [`permutation_importance`](@ref), [`nfoldCV_forest`](@ref).
