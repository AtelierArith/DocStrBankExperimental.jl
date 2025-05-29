```
tscv = TimeSeriesCV(; nfolds=4)
```

クロスバリデーションのリサンプリング戦略で、`evaluate!`、`evaluate`、およびチューニングで使用され、観測値が時間的に順序付けられており、独立していることが期待されない場合に使用されます。

```julia
train_test_pairs(tscv, rows)
```

`nfolds`の長さのイテレータを返し、各`train`と`test`は`rows`のサブベクター（行インデックス）のペアです。行は、最初のパーティションが最初のトレインセットであり、2番目のパーティションが最初のテストセットであるように、`nfolds + 1`のほぼ等しい長さのパーティションに順次分割されます。2番目のトレインセットは最初の2つのパーティションで構成され、2番目のテストセットは3番目のパーティションで構成され、各フォールドについてこのように続きます。

最初のパーティション（最初のトレインセット）は長さ`n + r`を持ち、ここで`n, r = divrem(length(rows), nfolds + 1)`であり、残りのパーティション（すべてのテストフォールド）は長さ`n`を持ちます。

# 例

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
