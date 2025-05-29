```
waterheight_total(q, equations)
```

与えられた一連の `equations` に対して、原始変数 `q` の総水深を返します。すなわち、[`waterheight`](@ref) $h$ と [`bathymetry`](@ref) $b$ の合計です。

`q` は単一のノードでの原始変数のベクトルであり、すなわち正しい長さ `nvariables(equations)` のベクトルです。
