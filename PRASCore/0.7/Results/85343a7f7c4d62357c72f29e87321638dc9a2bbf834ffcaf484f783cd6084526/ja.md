```
ショートフォール
```

`Shortfall` 結果仕様は、EUE や LOLE などの期待値に基づくリソース適合性リスク指標を報告し、`ShortfallResult` を生成します。

`ShortfallResult` は、地域名とタイムスタンプで直接インデックス指定することで、その地域とタイムステップにおける平均未供給エネルギーを推定するサンプル平均と標準偏差のタプルを取得できます。しかし、ほとんどの場合、標準リスク指標を直接取得するために [`EUE`](@ref) および [`LOLE`](@ref) コンストラクタを使用する方が簡単です。

例:

```julia
shortfall, =
    assess(sys, SequentialMonteCarlo(samples=1000), Shortfall())

period = ZonedDateTime(2020, 1, 1, 0, tz"UTC")

# 未供給エネルギーの平均と標準偏差
sf_mean, sf_std = shortfall["Region A", period]

# システム全体のリスク指標
eue = EUE(shortfall)
lole = LOLE(shortfall)
neue = NEUE(shorfall)

# 地域別リスク指標
regional_eue = EUE(shortfall, "Region A")
regional_lole = LOLE(shortfall, "Region A")
regional_neue = NEUE(shortfall, "Region A")

# 期間特有のリスク指標
period_eue = EUE(shortfall, period)
period_lolp = LOLE(shortfall, period)

# 地域および期間特有のリスク指標
period_eue = EUE(shortfall, "Region A", period)
period_lolp = LOLE(shortfall, "Region A", period)
```

サンプルレベルのショートフォール結果を記録するには、[`ShortfallSamples`](@ref) を参照してください。
