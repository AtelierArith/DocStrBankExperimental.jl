```
p = get_polynomial(graph::Compgraph)
```

計算グラフに基づく多項式を返します。`graph`は線形結合と乗算のみを含むと仮定されます。

`p`は、パッケージ[`Polynomials.jl`](https://juliamath.github.io/Polynomials.jl/stable/)の`Polynomial`型の多項式です。

また、[`get_polynomial_coefficients`](@ref)も参照してください。
