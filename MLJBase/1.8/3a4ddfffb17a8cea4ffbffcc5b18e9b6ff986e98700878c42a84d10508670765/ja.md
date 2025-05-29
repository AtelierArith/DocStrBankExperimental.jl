```
CompactPerformanceEvaluation <: AbstractPerformanceEvaluation
```

[`evaluate`](@ref)（モデルとデータ用）または[`evaluate!`](@ref)（マシン用）を`compact = true`オプションで呼び出したときに返されるオブジェクトの型。このようなオブジェクトは、デフォルトで返される[`PerformanceEvaluation`](@ref)オブジェクトと同じ構造を持っていますが、メモリを節約するために以下のフィールドが省略されています：`fitted_params_per_fold`、`report_per_fold`、`train_test_rows`。

残りのフィールドについては、[`PerformanceEvaluation`](@ref)を参照してください。
