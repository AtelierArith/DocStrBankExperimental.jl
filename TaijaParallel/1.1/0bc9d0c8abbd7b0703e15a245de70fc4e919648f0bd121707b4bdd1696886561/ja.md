```
TaijaBase.parallelize(
    parallelizer::ThreadsParallelizer,
    f::typeof(CounterfactualExplanations.Evaluation.evaluate),
    args...;
    kwargs...,
)
```

`f`の評価を`Threads.@threads`を使用して並列化します。この関数は反実的説明を評価するために使用されます。
