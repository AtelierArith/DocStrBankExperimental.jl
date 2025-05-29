```
StorageEnergy
```

`StorageEnergy`の結果仕様は、`Storages`の平均充電状態を報告し、`StorageEnergyResult`を生成します。

`StorageEnergyResult`は、ストレージデバイス名とタイムスタンプでインデックス付けされ、指定されたタイムステップにおけるそのストレージデバイスの平均エネルギーレベルを推定するためのサンプル平均と標準偏差のタプルを取得できます。

例:

```julia
storenergy, =
    assess(sys, SequentialMonteCarlo(samples=1000), StorageEnergy())

soc_mean, soc_std =
    storenergy["MyStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
```

サンプルレベルの充電状態については[`StorageEnergySamples`](@ref)を参照してください。

平均発電機-ストレージの充電状態については[`GeneratorStorageEnergy`](@ref)を参照してください。
