```
momentum(q, equations)
```

与えられた一連の `equations` に対して、原始変数 `q` の運動量/流出を返します。すなわち、[`waterheight`](@ref) と [`velocity`](@ref) の積です。

`q` は単一のノードでの原始変数のベクトルであり、すなわち正しい長さ `nvariables(equations)` のベクトルです。
