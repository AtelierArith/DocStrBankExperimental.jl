```
EulerEquations1D(; gravity, eta0 = 0.0)
```

与えられた重力加速度 `gravity` と静水面 `eta0` を持つ1Dオイラー方程式を表す構造体です。

!!! note
    DispersiveShallowWater.jlでは、オイラー方程式は*完全な線形分散関係*を計算するためにのみ使用されます

    $$
    \omega(k) = \sqrt{g k \tanh(h_0 k)},
    $$

    [`LinearDispersionRelation`](@ref) と [`wave_speed`](@ref) を参照してください。`EulerEquations1D` は方程式の系として解くことはできません。

