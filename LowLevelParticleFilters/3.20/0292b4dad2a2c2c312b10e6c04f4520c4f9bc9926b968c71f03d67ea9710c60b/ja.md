```
mode_trajectory(sol::ParticleFilteringSolution)
mode_trajectory(x::AbstractMatrix, we::AbstractMatrix)
```

粒子フィルタリングソリューションの軌道に沿ったモード（最大の重みを持つ粒子）を計算します。サイズ `T × nx` の行列を返します。
