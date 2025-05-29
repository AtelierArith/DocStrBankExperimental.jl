```
Matern32Kernel(; metric=Euclidean())
```

`metric` に関する $3/2$ 階の Matérn カーネル。

# 定義

入力 $x, x'$ と距離 $d(\cdot, \cdot)$ に対して、$3/2$ 階の Matérn カーネルは次のように与えられます。

$$
k(x, x') = \big(1 + \sqrt{3} d(x, x') \big) \exp\big(- \sqrt{3} d(x, x') \big).
$$

デフォルトでは、$d$ はユークリッド距離 $d(x, x') = \|x - x'\|_2$ です。

関連情報: [`MaternKernel`](@ref)
