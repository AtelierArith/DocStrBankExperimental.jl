```
next_collision(p::AbstractParticle, bd::Billiard) -> i, tmin, cp
```

`bd`内のすべての障害物に対して[`collision`](@ref)を計算し、最小のものを見つけます。衝突する障害物のインデックス、時間、および衝突点を返します。
