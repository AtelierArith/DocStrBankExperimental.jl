```
StorageEnergySamples
```

`StorageEnergySamples`の結果仕様は、`Storages`のサンプルレベルの充電状態を報告し、`StorageEnergySamplesResult`を生成します。

`StorageEnergySamplesResult`は、ストレージデバイス名とタイムスタンプでインデックス付けされ、指定されたタイムステップ内のデバイスのサンプルレベルの充電状態のベクトルを取得できます。

例:

```julia
storenergy, =
    assess(sys, SequentialMonteCarlo(samples=10), StorageEnergySamples())

samples = storenergy["MyStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10
```

この結果仕様は、大きなサンプルサイズに対して大量のメモリを必要とすることに注意してください。サンプルレベルの粒度が必要ない場合の推定平均ストレージ充電状態については、[`StorageEnergy`](@ref)を参照してください。
