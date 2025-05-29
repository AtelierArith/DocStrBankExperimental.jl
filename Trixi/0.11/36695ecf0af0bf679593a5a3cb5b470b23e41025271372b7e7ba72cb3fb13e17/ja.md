```
waterheight_pressure(u, equations)
```

保存された変数 `u` に関連する [`waterheight`](@ref) と [`pressure`](@ref) の積を返します。これは、与えられた `equations` のセットに対して行われます。例えば、[`ShallowWaterEquations2D`](@ref) の場合です。

`u` は、単一のノードでの保存された変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
