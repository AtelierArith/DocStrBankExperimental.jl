```
xgboost(data; num_round=10, watchlist=Dict(), kw...)
xgboost(data, ℓ′, ℓ″; kw...)
```

Creates an xgboost gradient booster object on training data `data` and runs `nrounds` of training. This is essentially an alias for constructing a [`Booster`](@ref) with `data` and keyword arguments followed by [`update!`](@ref) for `nrounds`.

`watchlist` is a dict the keys of which are strings giving the name of the data to watch and the values of which are [`DMatrix`](@ref) objects containing the data. It is mandatory to use an OrderedDict when utilising early*stopping*rounds and there is more than 1 element in watchlist to ensure XGBoost uses the  correct and intended dataset to perform early stop.

`early_stopping_rounds` activates early stopping if set to > 0. Validation metric needs to improve at  least once in every k rounds. If `watchlist` is not explicitly provided, it will use the training dataset  to evaluate the stopping criterion. Otherwise, it will use the last data element in `watchlist` and the last metric in `eval_metric` (if more than one). Note that `watchlist` cannot be empty if  `early_stopping_rounds` is enabled.

`maximize` If early*stopping*rounds is set, then this parameter must be set as well. When it is false, it means the smaller the evaluation score the better. When set to true, the larger the evaluation score the better.

All other keyword arguments are passed to [`Booster`](@ref).  With few exceptions these are model training hyper-parameters, see [here](https://xgboost.readthedocs.io/en/stable/parameter.html) for a comprehensive list.

A custom loss function can be provided via its first and second derivatives (`ℓ′` and `ℓ″` respectively). See [`updateone!`](@ref) for more details.

## Examples

```julia
# Example 1: Basic usage of XGBoost
(X, y) = (randn(100,3), randn(100))

b = xgboost((X, y), num_round=10, max_depth=10, η=0.1)

ŷ = predict(b, X)

# Example 2: Using early stopping (using a validation set) with a watchlist
dtrain = DMatrix((randn(100,3), randn(100)))
dvalid = DMatrix((randn(100,3), randn(100)))

watchlist = OrderedDict(["train" => dtrain, "valid" => dvalid])

b = xgboost(dtrain, num_round=10, early_stopping_rounds = 2, watchlist = watchlist, max_depth=10, η=0.1)

# note that ntree_limit in the predict function helps assign the upper bound for iteration_range in the XGBoost API 1.4+
ŷ = predict(b, dvalid, ntree_limit = b.best_iteration)
```
