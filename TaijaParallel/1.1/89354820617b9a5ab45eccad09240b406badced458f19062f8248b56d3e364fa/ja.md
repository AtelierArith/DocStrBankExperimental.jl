```
TaijaBase.parallelize(
    parallelizer::ThreadsParallelizer,
    f::typeof(CounterfactualExplanations.generate_counterfactual),
    args...;
    kwargs...,
)
```

`f`の評価を`Threads.@threads`を使用して並列化します。この関数は反事実的説明を生成するために使用されます。
