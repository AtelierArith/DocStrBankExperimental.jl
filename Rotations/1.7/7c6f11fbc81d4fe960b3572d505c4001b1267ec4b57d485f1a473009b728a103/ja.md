```
struct Angle2d{T} <: Rotation{2,T}
    theta::T
end
```

角度によってパラメータ化された2×2回転行列。`Angle2d`型の内部には角度のみが保存されており、`getindex`などの値はその場で計算されます。
