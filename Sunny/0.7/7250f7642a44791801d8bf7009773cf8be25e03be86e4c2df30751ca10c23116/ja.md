```
step!(sys::System, dynamics)
```

スピン構成を1つの動的時間ステップ進めます。`dynamics`オブジェクトは、[`Langevin`](@ref)や[`ImplicitMidpoint`](@ref)のような連続スピンダイナミクスであるか、または[`LocalSampler`](@ref)のような離散モンテカルロサンプリングスキームである可能性があります。
