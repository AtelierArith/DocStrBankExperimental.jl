```
calculate_feature_importance(method::Function, X::DataFrame, y::Vector)
```

Calculate feature importance defined by `method`. Similar with `select_features`, this can take `X` in `DataFrame` or splitted into `X_data` in `Matrix` and `X_features` in `Vector`.

This function will return `Dict` with feature names as key and scores as value.
