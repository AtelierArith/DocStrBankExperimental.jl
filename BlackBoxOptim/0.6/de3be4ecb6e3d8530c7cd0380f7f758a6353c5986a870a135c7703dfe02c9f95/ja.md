```
sync_fitness_update([f], job::AbstractFitnessEvaluationJob,
                    eval::AbstractAsyncEvaluator)
```

`job`のフィットネスが計算されるまで待機し、オプションで処理された各候補に`f`関数を適用します。

関連情報: [`async_update_fitness!`](@ref), [`update_fitness!`](@ref).
