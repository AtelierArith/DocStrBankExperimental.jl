```
NoiseRNG{N,T} <: AbstractRNG where {N,T<:AbstractNoise{N}}
```

ノイズ関数を `rand()` で使用するための rng として使用するラッパータイプ。

## フィールド

  * `noise::T` : ノイズ関数。
  * `counter::N = zero(N)` : 生成された数のシーケンスが現在どこにあるかを示すカウンター。

## 例

```jldoctest julia> rng = NoiseRNG(SquirrelNoise5()) NoiseRNG{UInt32, SquirrelNoise5}(SquirrelNoise5(0x00000000), 0x00000000)

julia> rand(rng) 0.08778560161590576 ````
