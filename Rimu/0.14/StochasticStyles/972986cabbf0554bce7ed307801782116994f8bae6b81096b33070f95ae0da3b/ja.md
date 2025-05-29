```
IsDeterministic{T=Float64}(compression=NoCompression()) <: StochasticStyle{T}
```

決定論的なベクトル行列の乗算を伝播します。結果のベクトル（消去後）の確率的圧縮は、オプションの `compression` 引数を関連する [`CompressionStrategy`](@ref) に設定することでトリガーできます。

また、[`StochasticStyle`](@ref) も参照してください。
