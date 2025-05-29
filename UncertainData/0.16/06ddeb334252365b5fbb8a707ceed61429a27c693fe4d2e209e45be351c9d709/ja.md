```
combine(uvals::Vector{AbstractUncertainValue}; n = 10000*length(uvals), 
    bw::Union{Nothing, Real} = nothing)
```

複数の不確実な値を単一の不確実な値に結合します。これは、`uvals`内の各不確実な値を`n`回サンプリングし、それらの引き出しをプールすることで行われます。最後に、これらの引き出しに対して最終分布のカーネル密度推定が計算されます。

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

combine(uvals)
combine(uvals, n = 20000) # 総引き出し数を調整
```
