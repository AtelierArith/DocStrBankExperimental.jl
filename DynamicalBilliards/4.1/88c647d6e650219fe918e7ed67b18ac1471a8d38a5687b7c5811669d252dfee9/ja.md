```
Wall{T<:AbstractFloat} <: Obstacle{T}
```

壁障害物のスーパタイプ。

すべての `Wall` サブタイプ（`PeriodicWall` を除く）は `Wall(sp, ep)` として呼び出すことができ、その場合、法線ベクトルは自動的に `v = ep - sp` の左側を指すように計算されます。
