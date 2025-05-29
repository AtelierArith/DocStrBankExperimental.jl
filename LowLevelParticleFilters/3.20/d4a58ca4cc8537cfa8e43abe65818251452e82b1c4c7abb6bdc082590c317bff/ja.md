```
mean_trajectory(sol::ParticleFilteringSolution)
mean_trajectory(x::AbstractMatrix, we::AbstractMatrix)
```

粒子フィルタリングソリューションの軌道に沿った加重平均を計算します。サイズ `T × nx` の行列を返します。`x` と `we` が供給される場合、重みは元の空間（対数空間ではなく）にあることが期待されます。

[`mode_trajectory`](@ref) も参照してください。
