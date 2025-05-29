```
evaluate!(m::ParallelModel, df::DataFrame)
```

`m.func`を`df`の各行に対して呼び出し、その結果を`DataFrame`の列`m.name`として追加します。`Distributed`を通じてワーカーが追加されると、行は並列に評価されます。
