```
利用率
```

`Utilization` 結果仕様は、`Interfaces` の推定平均絶対利用率を報告し、`UtilizationResult` を生成します。

`Flow` がインターフェースを介した平均方向性電力移動を報告するのに対し、`Utilization` はインターフェースの転送能力に対するフローの絶対値を報告します（ラインの停止の影響を考慮します）。例えば、対称的に制約されたインターフェースが完全に混雑しており、サンプルの半分で一方向に最大電力が流れ、残りのサンプルで反対方向に流れる場合、平均フローは 0 MW ですが、平均利用率は 100% になります。

`UtilizationResult` は、地域名の `Pair` とタイムスタンプでインデックス付けされ、インターフェースの平均利用率を推定するサンプル平均と標準偏差のタプルを取得できます。結果の絶対値の性質により、結果は方向に依存しません。`"Region A" => "Region B"` をクエリすると、`"Region B" => "Region A"` と同じ結果が得られます。

例:

```julia
utils, =
    assess(sys, SequentialMonteCarlo(samples=1000), Utilization())

util_mean, util_std =
    utils["Region A" => "Region B", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

util2_mean, util2_std =
    utils["Region B" => "Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert util_mean == util2_mean
```

サンプルレベルの利用率結果については、[`UtilizationSamples`](@ref) を参照してください。
