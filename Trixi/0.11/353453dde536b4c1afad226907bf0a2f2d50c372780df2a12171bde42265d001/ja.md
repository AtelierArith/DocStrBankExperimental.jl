```
energy_kinetic(u, equations)
```

与えられた `equations` のセットに対して、保存された変数 `u` の運動エネルギーを返します。例えば、[`CompressibleEulerEquations2D`](@ref) のように。

`u` は単一のノードでの保存された変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
