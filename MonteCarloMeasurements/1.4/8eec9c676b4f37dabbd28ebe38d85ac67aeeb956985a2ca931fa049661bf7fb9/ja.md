```
struct Particles{T, N} <: AbstractParticles{T, N}
```

この型は、粒子の雲を使用して不確実性を表します。

# コンストラクタ:

  * `Particles()`
  * `Particles(N::Integer)`
  * `Particles([rng::AbstractRNG,] d::Distribution)`
  * `Particles([rng::AbstractRNG,] N::Integer, d::Distribution; permute=true, systematic=true)`
  * `Particles(v::Vector{T} where T)`
  * `Particles(m::Matrix{T} where T)`: 多変量粒子を作成します (Vector{Particles})
