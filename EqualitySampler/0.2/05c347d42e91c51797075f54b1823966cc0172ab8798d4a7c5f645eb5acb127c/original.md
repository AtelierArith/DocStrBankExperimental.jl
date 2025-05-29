```julia
proportion_test(ns::AbstractVector{<:Integer}, ks::AbstractVector{<:Integer}, args...; kwargs...)
proportion_test(obj::SuffstatsProportions, method::AbstractSamplingMethod, partition_prior::AbstractPartitionDistribution;
    α::Number = 1.0, β::Number = 1.0, verbose::Bool = true, threaded::Bool = true)
```

Conduct a proportion test for a given set of data.

```
The method should be one of `Enumerate`, `EnumerateThenSample`, `SampleIntegrated`, or `SampleRJMCMC`.
```

The return type depends on the method used. Specifically, `Enumerate` returns an `EnumerateResult`, `EnumerateThenSample` returns an `EnumerateThenSampleResult`, `SampleIntegrated` returns an `IntegratedResult`, and `SampleRJMCMC` returns an `RJMCMCResult`. These different types do not really matter and are mostly used to make various extractor functions work.

`α` and `β` correspond to the hyperparameters of the Beta prior distribution for the proportions.
