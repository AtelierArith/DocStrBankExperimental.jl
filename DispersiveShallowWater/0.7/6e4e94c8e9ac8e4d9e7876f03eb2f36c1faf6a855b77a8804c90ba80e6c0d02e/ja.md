```
energy_total(q, equations)
```

与えられた一連の `equations` に対して、原始変数 `q` の総エネルギーを返します。すべての [`AbstractShallowWaterEquations`](@ref) において、総エネルギーは浅水サブシステムの運動エネルギーと位置エネルギーの合計として与えられます。すなわち、

$$
\frac{1}{2} h v^2 + \frac{1}{2} g \eta^2
$$

1Dの場合、ここで $h$ は [`waterheight`](@ref)、$\eta = h + b$ は [`waterheight_total`](@ref)、$v$ は [`velocity`](@ref)、$g$ は [`gravity`](@ref) です。

`q` は単一のノードにおける原始変数のベクトルであり、すなわち、正しい長さ `nvariables(equations)` のベクトルです。
