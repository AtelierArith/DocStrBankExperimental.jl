```
combine(uvals::Vector{AbstractUncertainValue}, weights::ProbabilityWeights; 
    n = 10000*length(uvals), 
    bw::Union{Nothing, Real} = nothing)
```

複数の不確実な値を単一の不確実な値に結合します。これは、提供された相対的な解析的`weights`に従って、`uvals`内の各不確実な値を再サンプリングすることによって行われます。これにより、相対的重要性が示されます（デフォルトでは正規化されているため、1に合計する必要はありません）。次に、これらのサンプルをまとめます。最後に、最終的な分布に対してカーネル密度推定が`n`の合計サンプルに対して計算されます。

`ProbabilityWeights`を提供すると、`AnalyticWeights`と同じ動作が得られますが、たとえば、重みが定量的に決定された場合には、より適切かもしれません。

KDEのバンド幅は`bw`によって制御されます。デフォルトでは、`bw = nothing`です。この場合、バンド幅は`KernelDensity.default_bandwidth`関数を使用して決定されます。

!!! tip
    非常に広い、正規分布に近い分布の場合、デフォルトのバンド幅がうまく機能することがあります。ただし、非常に尖った分布や離散的な集団を結合する場合は、バンド幅を大幅に下げることを検討してください。


# 例

```julia
v1 = UncertainValue(Normal, 1, 0.3)
v2 = UncertainValue(Normal, 0.8, 0.4)
v3 = UncertainValue([rand() for i = 1:3], [0.3, 0.3, 0.4])
v4 = UncertainValue(Normal, 3.7, 0.8)
uvals = [v1, v2, v3, v4];

# 2つの異なる構文オプション
combine(uvals, ProbabilityWeights([0.2, 0.1, 0.3, 0.2]))
combine(uvals, pweights([0.2, 0.1, 0.3, 0.2]), n = 20000) # 合計サンプル数を調整
```
