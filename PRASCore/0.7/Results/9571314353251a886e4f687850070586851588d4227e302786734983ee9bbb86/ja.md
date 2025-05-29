```
GeneratorStorageAvailability
```

`GeneratorStorageAvailability` の結果仕様は、`GeneratorStorages` のサンプルレベルの離散的な可用性を報告し、`GeneratorStorageAvailabilityResult` を生成します。

`GeneratorStorageAvailabilityResult` は、発電機ストレージ名とタイムスタンプでインデックス付けされ、指定されたタイムステップにおけるユニットのサンプルレベルの可用性状態のベクトルを取得できます。状態はブール値で提供され、`true` はユニットが利用可能であることを示し、`false` は利用できないことを示します。

例:

```julia
genstoravail, =
    assess(sys, SequentialMonteCarlo(samples=10), GeneratorStorageAvailability())

samples = genstoravail["MyGenerator123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Bool}
@assert length(samples) == 10
```
