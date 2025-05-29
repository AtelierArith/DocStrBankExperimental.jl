```
function interpolate_weno4(
    xs::AbstractVector{<:Number},
    xp::AbstractVector{<:Number},
    fp::AbstractVector{<:Number};
    extrapolate=false
)
```

1D補間を行う関数で、第四次重み付き本質的非振動（WENO）スキームを使用しています。詳細は[Janett et al (2019)](https://ui.adsabs.harvard.edu/abs/2019A%26A...624A.104J/abstract)を参照してください。Chris Osborneによるhttps://github.com/Goobley/Weno4Interpolationに基づいています。

# 引数

  * `xs::AbstractVector{<:Number}`: 補間された値を評価するx座標
  * `xp::AbstractVector{<:Number}`: データポイントのx座標。少なくとも4つの要素を持ち、増加しており、NaNを含んではいけません。
  * `fp::AbstractVector{<:Number}`: データポイントのy座標。`xp`と同じ長さでなければなりません。

# キーワード

  * `extrapolate::Bool`: 外挿を使用するかどうか。`true`の場合、端点から二次外挿を行います。`false`の場合、`xs`が`xp`の外にある場合でもエラーは発生せず、最も近い`fp`値が返されます。
