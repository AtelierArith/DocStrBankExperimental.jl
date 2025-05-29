```
FlowSamples
```

`FlowSamples` の結果仕様は、`Interfaces` を横断する電力フローのサンプルレベルの大きさと方向を報告し、`FlowSamplesResult` を生成します。

`FlowSamplesResult` は、方向性のある地域名の `Pair` とタイムスタンプでインデックス付けされ、指定された方向性インターフェースに対するサンプルレベルのネットフローの大きさと方向のベクトルを取得します。 `"Region A" => "Region B"` のクエリの場合、1つのサンプルのフローが A から B へのものであれば、報告される値は正となり、逆方向、すなわち B から A へのフローであれば、値は負となります。

例:

```julia
flows, =
    assess(sys, SequentialMonteCarlo(samples=10), FlowSamples())

samples = flows["Region A" => "Region B", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10

samples2 = flows["Region B" => "Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples == -samples2
```

この結果仕様は、大きなサンプルサイズに対して大量のメモリを必要とすることに注意してください。サンプルレベルの粒度が必要ない場合の推定平均フロー結果については、[`Flow`](@ref) を参照してください。
