```julia
struct InitialTrajectory{K<:BaytesFilters.ParticleKernel, C<:BaytesFilters.ParticleReferencing, M<:BaytesFilters.ParticleFilterMemory}
```

サンプリングプロセスのための参照軌道を取得する情報を含みます。

# フィールド

  * `kernel::BaytesFilters.ParticleKernel`: 粒子伝播のためのカーネル
  * `referencing::BaytesFilters.ParticleReferencing`: 参照方法
  * `memory::BaytesFilters.ParticleFilterMemory`: PFにおける観測データと潜在データのためのメモリ。
