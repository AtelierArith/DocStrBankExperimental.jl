```
sample!(stochasticprogram::StochasticProgram, stage::Integer, sampler::AbstractSampler, n::Integer)
```

`samples`を使用して`n`のシナリオをサンプリングし、`stage`で`stochasticprogram`に追加します。`stochasticprogram`が分散している場合、シナリオはワーカー間で均等に分配されます。
