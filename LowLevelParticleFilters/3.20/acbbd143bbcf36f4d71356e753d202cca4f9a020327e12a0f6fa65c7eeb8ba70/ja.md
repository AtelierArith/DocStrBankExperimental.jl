```
ParticleFilter(N::Integer, dynamics, measurement, dynamics_density, measurement_density, initial_density; threads = false, p = NullParameters(), kwargs...)
```

詳細については、ドキュメントを参照してください: https://baggepinnen.github.io/LowLevelParticleFilters.jl/stable/#Particle-filter-1

# 引数:

  * `N`: 粒子の数
  * `dynamics`: 離散時間の動力学関数 `(x, u, p, t) -> x⁺`
  * `measurement`: 測定関数 `(x, u, p, t) -> y`
  * `dynamics_density`: 動力学における加法的ノイズの確率密度関数。非加法的ノイズには [`AdvancedParticleFilter`](@ref) を使用してください。
  * `measurement_density`: 測定ノイズの加法的確率密度関数。非加法的ノイズには [`AdvancedParticleFilter`](@ref) を使用してください。
  * `initial_density`: 初期状態の分布。
