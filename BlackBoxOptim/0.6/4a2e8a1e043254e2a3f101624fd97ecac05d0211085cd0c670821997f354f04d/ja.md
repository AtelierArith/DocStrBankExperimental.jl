```
async_update_fitness!(eval::AbstractAsyncEvaluator, candidates::Any;
                      force::Bool=false) ->
                      Union{AbstractFitnessEvaluationJob, Nothing}
```

非同期でフィットネスを計算します。*candidates* は `iterate()` インターフェースをサポートし、[`Candidate`](@ref) 要素を返す必要があります。

[`AbstractFitnessEvaluationJob`](@ref) を返すか、*candidates* に候補が含まれていない場合は `nothing` を返します。

# 引数

  * `force::Bool`: 候補がすでに非NAフィットネスを持っている場合でもフィットネス計算を強制します

関連情報: [`sync_update_fitness`](@ref)
