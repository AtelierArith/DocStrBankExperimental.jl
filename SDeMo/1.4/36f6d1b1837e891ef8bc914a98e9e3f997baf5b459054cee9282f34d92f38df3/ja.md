```
explain(model::AbstractSDM, j; observation = nothing, instances = nothing, samples = 100, kwargs..., )
```

MCMC近似のシャプレー値を使用して、特定の予測に対する説明を提供します。第二引数 `j` は、説明を提供する変数です。

`observation` キーワードは、説明を提供する必要がある `instances` データセットの行です。`instances` が `nothing` の場合、説明はトレーニングデータに対して行われます。

他のすべてのキーワード引数は `predict` に渡されます。
