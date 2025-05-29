```julia
ModifyGauge!(lat::Lattice{T}, A::Function ; n::Int64 = 100, _kwargs::Dict = Dict()) where{T}
```

格子 `lat` の固定ゲージベクトルポテンシャル `A` を使用して格子のホッピングを修正し、対応する位相因子でボンド行列を乗算します。
