```julia
anova_test(f::StatsModels.FormulaTerm, df::DataFrames.DataFrame, args..., ; kwargs...)
anova_test(y::AbstractVector{<:Number}, g::AbstractVector{<:Integer}, args..., ; kwargs...)
anova_test(y::AbstractVector{<:Number}, g::AbstractVector{<:Integer}, args..., ; kwargs...)
anova_test(y_means::AbstractVector{<:Number}, y_vars::AbstractVector{<:Number}, ns::AbstractVector{<:Integer}, args..., ; kwargs...)
anova_test(obj::SuffstatsANOVA, method::AbstractSamplingMethod, prior::AbstractPartitionDistribution; rscale::Number = 1.0, verbose::Bool = true, threaded::Bool = false)
```

Conduct a one way anova test.

Data can be input in four ways.

1. using a formula and dataframe (`@formula(outcome ~ 1 + grouping), df`).
2. rawdata and vector of group membership (`y = randn(6), g = [1, 1, 2, 2, 3, 3]`).
3. rawdata and group ranges (`y = randn(6), g = [1:2, 3:4, 5:6]`)
4. means, variances, and group sizes (`y_means = randn(3), y_vars = randexp(3), ns  = rand(2:2, 3)`).

In each case, the data is reduced to an object of type `SuffstatsANOVA` which contains the sufficient statistics for the test.

The method should be one of `Enumerate`, `EnumerateThenSample`, `SampleIntegrated`, or `SampleRJMCMC`. The return type depends on the method used. Specifically, `Enumerate` returns an `EnumerateResult`, `EnumerateThenSample` returns an `EnumerateThenSampleResult`, `SampleIntegrated` returns an `IntegratedResult`, and `SampleRJMCMC` returns an `RJMCMCResult`. These different types do not really matter and are mostly used to make various extractor functions work.

For `EnumerateThenSample` and `SampleRJMCMC`, the raw posterior samples can be found inside the field `parameter_samples`, see also `AnovaParameterSamples`.
