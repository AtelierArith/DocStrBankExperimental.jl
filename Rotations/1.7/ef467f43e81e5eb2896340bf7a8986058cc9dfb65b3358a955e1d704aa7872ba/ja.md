```
struct RotationVec{T} <: Rotation{3,T}
RotationVec(sx, sy, sz)
```

3×3 回転行列のロドリゲスベクトルパラメータ化。ベクトル [sx, sy, sz] の方向が回転軸を定義し、回転角はそのノルムによって与えられます。
