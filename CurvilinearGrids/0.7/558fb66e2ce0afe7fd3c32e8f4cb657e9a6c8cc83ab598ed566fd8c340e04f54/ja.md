```
estimate_wall_distance(
```

ρ::Unitful.Density,   U::Unitful.Velocity,   L::Unitful.Length,   μ::Unitful.DynamicViscosity,   y_plus, )

入力条件に基づいて乱流境界層を捕捉するために必要な壁の厚さを推定します。これは (reynolds*number, wall*thickness) を返します。
