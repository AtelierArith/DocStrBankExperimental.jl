```
UtilizationSamples
```

`UtilizationSamples` の結果仕様は、`Interfaces` のサンプルレベルの絶対利用率を報告し、`UtilizationSamplesResult` を生成します。

`FlowSamples` がインターフェースを介した方向性の電力移転を報告するのに対し、`UtilizationSamples` はインターフェースの転送能力に対するフローの絶対値を報告します（ラインの停止の影響を考慮）。例えば、完全に混雑した100 MWの対称制約インターフェースは、+100または-100 MWのフローを持つ可能性がありますが、いずれの場合も利用率は100%になります。インターフェース内の50 MWのラインが停止した場合、フローは+50または-50 MWに減少する可能性がありますが、利用率は100%のままです。

`UtilizationSamplesResult` は、地域名の `Pair` とタイムスタンプでインデックス付けされ、そのタイムステップにおけるインターフェースのサンプルレベルの利用率のベクトルを取得できます。結果の絶対値の性質により、結果は方向に依存しません。`"Region A" => "Region B"` をクエリすると、`"Region B" => "Region A"` と同じ結果が得られます。

例:

```julia
utils, =
    assess(sys, SequentialMonteCarlo(samples=10), UtilizationSamples())

samples =
    utils["Region A" => "Region B", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10

samples2 =
    utils["Region B" => "Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples == samples2
```

この結果仕様は、大きなサンプルサイズに対して大量のメモリを必要とすることに注意してください。サンプルレベルの粒度が必要ない場合は、[`Utilization`](@ref) を参照してサンプル平均の利用率結果を確認してください。
