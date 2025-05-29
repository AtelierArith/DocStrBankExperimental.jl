```julia
anova_test(f::StatsModels.FormulaTerm, df::DataFrames.DataFrame, args..., ; kwargs...)
anova_test(y::AbstractVector{<:Number}, g::AbstractVector{<:Integer}, args..., ; kwargs...)
anova_test(y::AbstractVector{<:Number}, g::AbstractVector{<:Integer}, args..., ; kwargs...)
anova_test(y_means::AbstractVector{<:Number}, y_vars::AbstractVector{<:Number}, ns::AbstractVector{<:Integer}, args..., ; kwargs...)
anova_test(obj::SuffstatsANOVA, method::AbstractSamplingMethod, prior::AbstractPartitionDistribution; rscale::Number = 1.0, verbose::Bool = true, threaded::Bool = false)
```

一元ANOVAテストを実施します。

データは4つの方法で入力できます。

1. フォーミュラとデータフレームを使用する（`@formula(outcome ~ 1 + grouping), df`）。
2. 生データとグループメンバーシップのベクターを使用する（`y = randn(6), g = [1, 1, 2, 2, 3, 3]`）。
3. 生データとグループ範囲を使用する（`y = randn(6), g = [1:2, 3:4, 5:6]`）。
4. 平均、分散、およびグループサイズを使用する（`y_means = randn(3), y_vars = randexp(3), ns  = rand(2:2, 3)`）。

各ケースで、データはテストのための十分統計量を含む`SuffstatsANOVA`型のオブジェクトに還元されます。

メソッドは`Enumerate`、`EnumerateThenSample`、`SampleIntegrated`、または`SampleRJMCMC`のいずれかである必要があります。戻り値の型は使用されるメソッドによって異なります。具体的には、`Enumerate`は`EnumerateResult`を返し、`EnumerateThenSample`は`EnumerateThenSampleResult`を返し、`SampleIntegrated`は`IntegratedResult`を返し、`SampleRJMCMC`は`RJMCMCResult`を返します。これらの異なる型はあまり重要ではなく、主にさまざまな抽出関数が機能するように使用されます。

`EnumerateThenSample`および`SampleRJMCMC`の場合、生の事後サンプルはフィールド`parameter_samples`内に見つけることができます。`AnovaParameterSamples`も参照してください。
