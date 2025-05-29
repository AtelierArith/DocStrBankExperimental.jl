```
pressure(u, equations)
```

保存された変数 `u` に関連する圧力を、与えられた `equations` のセットに対して返します。例えば、[`CompressibleEulerEquations2D`](@ref) のように。

`u` は単一のノードでの保存された変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
