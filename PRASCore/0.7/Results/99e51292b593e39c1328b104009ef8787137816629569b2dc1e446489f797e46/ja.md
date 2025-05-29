```
フロー
```

`Flow` 結果仕様は、伝送 `Interfaces` 全体の推定平均フローを報告し、`FlowResult` を生成します。

`FlowResult` は、地域名の方向性 `Pair` とタイムスタンプでインデックス付けされ、サンプル平均と標準偏差のタプルを取得して、指定された方向性インターフェースに対するそのタイムステップでの平均ネットフローの大きさと方向を推定します。 `"Region A" => "Region B"` のクエリの場合、推定された平均フローが A から B へのものであれば、報告される値は正となり、平均フローが逆方向、すなわち B から A へのものであれば、値は負となります。

例:

```julia
flows, =
    assess(sys, SequentialMonteCarlo(samples=1000), Flow())

flow_mean, flow_std =
    flows["Region A" => "Region B", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
flow2_mean, flow2_std =
    flows["Region B" => "Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
@assert flow_mean == -flow2_mean
```

サンプルレベルのフロー結果については、[`FlowSamples`](@ref) を参照してください。
