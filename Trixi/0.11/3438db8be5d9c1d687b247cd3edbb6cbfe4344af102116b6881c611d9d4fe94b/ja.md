```
waterheight(u, equations)
```

保存された変数 `u` に関連する水の高さを、与えられた `equations` のセットに対して返します。例えば、[`ShallowWaterEquations2D`](@ref) のように。

`u` は、単一のノードでの保存された変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
