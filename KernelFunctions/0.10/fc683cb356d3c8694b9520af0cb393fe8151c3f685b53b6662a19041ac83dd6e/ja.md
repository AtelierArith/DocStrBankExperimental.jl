```
ExponentialKernel(; metric=Euclidean())
```

`metric`に関する指数カーネル。

# 定義

入力 $x, x'$ と距離 $d(\cdot, \cdot)$ に対して、指数カーネルは次のように定義されます。

$$
k(x, x') = \exp\big(- d(x, x')\big).
$$

デフォルトでは、$d$ はユークリッド距離 $d(x, x') = \|x - x'\|_2$ です。

関連情報: [`GammaExponentialKernel`](@ref)
