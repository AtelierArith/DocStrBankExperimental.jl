```
entropy(q, equations)
```

与えられた `equations` のセットに対して、原始変数 `q` のエントロピーを返します。すべての [`AbstractShallowWaterEquations`](@ref) に対して、`entropy` は単に [`energy_total`](@ref) です。

`q` は単一のノードでの原始変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
