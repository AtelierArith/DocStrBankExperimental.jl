```julia
proportion_test(ns::AbstractVector{<:Integer}, ks::AbstractVector{<:Integer}, args...; kwargs...)
proportion_test(obj::SuffstatsProportions, method::AbstractSamplingMethod, partition_prior::AbstractPartitionDistribution;
    α::Number = 1.0, β::Number = 1.0, verbose::Bool = true, threaded::Bool = true)
```

与えられたデータセットに対して比例検定を実施します。

```
メソッドは `Enumerate`、`EnumerateThenSample`、`SampleIntegrated`、または `SampleRJMCMC` のいずれかである必要があります。
```

戻り値の型は使用されるメソッドによって異なります。具体的には、`Enumerate` は `EnumerateResult` を返し、`EnumerateThenSample` は `EnumerateThenSampleResult` を返し、`SampleIntegrated` は `IntegratedResult` を返し、`SampleRJMCMC` は `RJMCMCResult` を返します。これらの異なる型はそれほど重要ではなく、主にさまざまな抽出関数が機能するために使用されます。

`α` と `β` は比例のベータ事前分布のハイパーパラメータに対応します。
