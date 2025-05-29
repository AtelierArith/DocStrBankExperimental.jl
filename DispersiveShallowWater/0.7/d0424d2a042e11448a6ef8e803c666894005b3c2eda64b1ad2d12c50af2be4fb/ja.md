```
prim2phys(q, equations)
```

原始変数 `q` を、与えられた `equations` の物理的に意味のある変数に変換します。デフォルトでは、これはほとんどの方程式に対して [`prim2prim`](@ref) と同じです。しかし、[`HyperbolicSerreGreenNaghdiEquations1D`](@ref) のような一部の方程式は、別の方程式のハイパーボリック近似であるため、変数の削減されたセットを返します（この場合は [`SerreGreenNaghdiEquations1D`](@ref)）。

また、[`is_hyperbolic_appproximation`](@ref) および [`hyperbolic_approximation_limit`](@ref) も参照してください。

`q` は、正しい長さ `nvariables(equations)` のベクトル型です。効率のためにエラーチェックを含まないため、入力が正しいことを確認してください。
