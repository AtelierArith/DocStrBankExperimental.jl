```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, n::Int)
```

与えられた [`AbstractPhaseSpacePoint`](@ref) において、方向 `dir` を持つ `n` 番目の粒子の運動量を返します。`n` がこの位相空間点の有効範囲外である場合、`BoundsError` がスローされます。
