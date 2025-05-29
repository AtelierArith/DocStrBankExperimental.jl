```
余剰
```

`余剰`結果仕様は、`Regions`の未使用の発電およびストレージ放出能力を報告し、`SurplusResult`を生成します。

`SurplusResult`は、地域名とタイムスタンプでインデックス付けされ、特定の地域とタイムステップにおける平均未使用容量を推定するためのサンプル平均と標準偏差のタプルを取得できます。

例:

```julia
surplus, =
    assess(sys, SequentialMonteCarlo(samples=1000), Surplus())

surplus_mean, surplus_std =
    surplus["Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
```

サンプルレベルの余剰結果については、[`SurplusSamples`](@ref)を参照してください。
