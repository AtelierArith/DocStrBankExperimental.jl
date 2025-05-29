```
c = get_polynomial_coefficients(graph::Compgraph)
```

計算グラフに基づく多項式の係数を返します。`graph`は線形結合と乗算のみを含むと仮定されます。

係数`c`は、単項式基底で表現された係数を含むベクトルであり、主係数から定数項までソートされています。

詳細は[`get_polynomial`](@ref)を参照してください。
