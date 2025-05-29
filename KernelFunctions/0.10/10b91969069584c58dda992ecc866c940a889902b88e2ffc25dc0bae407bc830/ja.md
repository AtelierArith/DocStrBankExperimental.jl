```
Matern52Kernel(; metric=Euclidean())
```

`metric`に関する$5/2$階のマテールンカーネル。

# 定義

入力$x, x'$および距離$d(\cdot, \cdot)$に対して、$5/2$階のマテールンカーネルは次のように与えられます。

$$
k(x, x') = \bigg(1 + \sqrt{5} d(x, x') + \frac{5}{3} d(x, x')^2\bigg)
           \exp\big(- \sqrt{5} d(x, x') \big).
$$

デフォルトでは、$d$はユークリッド距離$d(x, x') = \|x - x'\|_2$です。

関連情報: [`MaternKernel`](@ref)
