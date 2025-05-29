```
sample!(stochasticprogram::TwoStageStochasticProgram, sampler::AbstractSampler, n::Integer)
```

`sampler`を使用して`n`シナリオをサンプリングし、二段階の`stochasticprogram`に追加します。`stochasticprogram`が分散している場合、シナリオはワーカー間で均等に分配されます。
