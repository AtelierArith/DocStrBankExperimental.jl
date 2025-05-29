```
random_velocities!(sys, temp; rng=Random.default_rng())
random_velocities!(vels, sys, temp; rng=Random.default_rng())
```

[`System`](@ref)の速度、またはベクトルの速度を、マクスウェル-ボルツマン分布から生成されたランダムな速度に設定します。
