```
AMORS.apply_scaling_factor!(α::Real, x, y) -> α
```

スカラー `α` で `x` のエントリをインプレースで乗算し、`y` のエントリを `inv(α)` で乗算します。`α` を返します。[`AMORS.scale!`](@ref) を参照してください。
