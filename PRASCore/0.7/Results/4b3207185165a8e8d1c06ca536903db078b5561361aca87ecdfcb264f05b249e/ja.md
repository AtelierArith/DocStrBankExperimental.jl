```
ShortfallSamples
```

`ShortfallSamples` の結果仕様は、サンプルレベルの未供給エネルギーの結果を報告し、`ShortfallSamplesResult` を生成します。

`ShortfallSamplesResult` は、地域名とタイムスタンプで直接インデックス指定することで、その地域とタイムステップにおけるサンプルレベルの未供給エネルギー結果のベクトルを取得できます。 [`EUE`](@ref) および [`LOLE`](@ref) コンストラクタも、標準的なリスク指標を取得するために使用できます。

例:

```julia
shortfall, =
    assess(sys, SequentialMonteCarlo(samples=10), ShortfallSamples())

period = ZonedDateTime(2020, 1, 1, 0, tz"UTC")

samples = shortfall["Region A", period]

@assert samples isa Vector{Float64}
@assert length(samples) == 10

# システム全体のリスク指標
eue = EUE(shortfall)
lole = LOLE(shortfall)
neue = NEUE(shortfall)

# 地域別のリスク指標
regional_eue = EUE(shortfall, "Region A")
regional_lole = LOLE(shortfall, "Region A")
regional_neue = NEUE(shortfall, "Region A")

# 特定の期間のリスク指標
period_eue = EUE(shortfall, period)
period_lolp = LOLE(shortfall, period)

# 地域および期間特有のリスク指標
period_eue = EUE(shortfall, "Region A", period)
period_lolp = LOLE(shortfall, "Region A", period)
```

この結果仕様は、大きなサンプルサイズに対して大量のメモリを必要とすることに注意してください。サンプルレベルの粒度が必要ない場合の平均的なショートフォール結果については、[`Shortfall`](@ref) を参照してください。
