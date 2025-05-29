```
GeneratorStorageEnergy
```

`GeneratorStorageEnergy`の結果仕様は、`GeneratorStorages`の平均充電状態を報告し、`GeneratorStorageEnergyResult`を生成します。

`GeneratorStorageEnergyResult`は、発電機ストレージデバイス名とタイムスタンプでインデックス化でき、指定されたタイムステップにおけるその発電機ストレージデバイスの平均エネルギーレベルを推定するためのサンプル平均と標準偏差のタプルを取得します。

例:

```julia
genstorenergy, =
    assess(sys, SequentialMonteCarlo(samples=1000), GeneratorStorageEnergy())

soc_mean, soc_std =
    genstorenergy["MyGeneratorStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
```

サンプルレベルの発電機ストレージ充電状態については[`GeneratorStorageEnergySamples`](@ref)を参照してください。

平均ストレージ充電状態については[`StorageEnergy`](@ref)を参照してください。
