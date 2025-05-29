```
density_pressure(u, equations)
```

保存された変数 `u` に関連する [`density`](@ref) と [`pressure`](@ref) の積を返します。これは、例えば [`CompressibleEulerEquations2D`](@ref) のような特定の `equations` のセットに対して有用です。これは、例えば（衝撃捕捉またはAMR）指標の変数として役立ちます。

`u` は、単一のノードでの保存された変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
