```
SurplusSamples
```

`SurplusSamples`の結果仕様は、`Regions`のサンプルレベルの未使用生成およびストレージ放出能力を報告し、`SurplusSamplesResult`を生成します。

`SurplusSamplesResult`は、地域名とタイムスタンプでインデックス付けされ、その地域とタイムステップにおけるサンプルレベルの余剰値のベクトルを取得できます。

例:

```julia
surplus, =
    assess(sys, SequentialMonteCarlo(samples=10), SurplusSamples())

samples = surplus["Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10
```

この結果仕様は、大きなサンプルサイズに対して大量のメモリを必要とすることに注意してください。サンプルレベルの粒度が必要ない場合の推定平均余剰値については、[`Surplus`](@ref)を参照してください。
