```
tscv = TimeSeriesCV(; nfolds=4)
```

Cross-validation resampling strategy, for use in `evaluate!`, `evaluate` and tuning, when observations are chronological and not expected to be independent.

```julia
train_test_pairs(tscv, rows)
```

Returns an `nfolds`-length iterator of `(train, test)` pairs of vectors (row indices), where each `train` and `test` is a sub-vector of `rows`. The rows are partitioned sequentially into `nfolds + 1` approximately equal length partitions, where the first partition is the first train set, and the second partition is the first test set. The second train set consists of the first two partitions, and the second test set consists of the third partition, and so on for each fold.

The first partition (which is the first train set) has length `n + r`, where `n, r = divrem(length(rows), nfolds + 1)`, and the remaining partitions (all of the test folds) have length `n`.

# Examples

```julia-repl
julia> MLJBase.train_test_pairs(TimeSeriesCV(nfolds=3), 1:10)
3-element Vector{Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 (1:4, 5:6)
 (1:6, 7:8)
 (1:8, 9:10)

julia> model = (@load RidgeRegressor pkg=MultivariateStats verbosity=0)();

julia> data = @load_sunspots;

julia> X = (lag1 = data.sunspot_number[2:end-1],
            lag2 = data.sunspot_number[1:end-2]);

julia> y = data.sunspot_number[3:end];

julia> tscv = TimeSeriesCV(nfolds=3);

julia> evaluate(model, X, y, resampling=tscv, measure=rmse, verbosity=0)
┌───────────────────────────┬───────────────┬────────────────────┐
│ _.measure                 │ _.measurement │ _.per_fold         │
├───────────────────────────┼───────────────┼────────────────────┤
│ RootMeanSquaredError @753 │ 21.7          │ [25.4, 16.3, 22.4] │
└───────────────────────────┴───────────────┴────────────────────┘
_.per_observation = [missing]
_.fitted_params_per_fold = [ … ]
_.report_per_fold = [ … ]
_.train_test_rows = [ … ]
```
