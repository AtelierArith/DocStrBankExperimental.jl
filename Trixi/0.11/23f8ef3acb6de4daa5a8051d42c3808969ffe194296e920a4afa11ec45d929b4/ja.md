```
density(u, equations)
```

与えられた一連の `equations` に対して、保存された変数 `u` に関連する密度を返します。例えば、[`CompressibleEulerEquations2D`](@ref) のように。

`u` は単一のノードでの保存された変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
