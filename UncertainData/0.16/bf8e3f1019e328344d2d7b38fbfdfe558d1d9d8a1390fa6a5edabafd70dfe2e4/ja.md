```
combine(uvals::Vector{AbstractUncertainValue}, weights::FrequencyWeights;
    bw::Union{Nothing, Real} = nothing)
```

複数の不確実な値を単一の不確実な値に結合します。これは、`uvals`内の各不確実な値をその相対頻度（`weights`によって提供される絶対的な引き数の数）に従って再サンプリングすることによって行われます。最後に、最終的な分布に対してカーネル密度推定が`sum(weights)`の合計引き数に対して計算されます。

KDEのバンド幅は`bw`によって制御されます。デフォルトでは、`bw = nothing`です。この場合、バンド幅は`KernelDensity.default_bandwidth`関数を使用して決定されます。

!!! tip
    非常に広く、正規分布に近い分布の場合、デフォルトのバンド幅がうまく機能することがあります。ただし、非常に尖った分布や離散的な集団を結合する場合は、バンド幅を大幅に下げることを検討してください。


# 例

```julia
v1 = UncertainValue(Normal, 1, 0.3)
v2 = UncertainValue(Normal, 0.8, 0.4)
v3 = UncertainValue([rand() for i = 1:3], [0.3, 0.3, 0.4])
v4 = UncertainValue(Normal, 3.7, 0.8)
uvals = [v1, v2, v3, v4];

# 2つの異なる構文オプション
combine(uvals, FrequencyWeights([100, 500, 343, 7000]))
combine(uvals, pweights([1410, 550, 223, 801]))
```
