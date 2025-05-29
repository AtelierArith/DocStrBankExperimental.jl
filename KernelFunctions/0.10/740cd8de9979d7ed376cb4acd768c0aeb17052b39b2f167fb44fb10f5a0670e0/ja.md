```
SqExponentialKernel(; metric=Euclidean())
```

平方指数カーネルは `metric` に関して定義されます。

# 定義

入力 $x, x'$ と距離 $d(\cdot, \cdot)$ に対して、平方指数カーネルは次のように定義されます。

$$
k(x, x') = \exp\bigg(- \frac{d(x, x')^2}{2}\bigg).
$$

デフォルトでは、$d$ はユークリッド距離 $d(x, x') = \|x - x'\|_2$ です。

関連情報: [`GammaExponentialKernel`](@ref)
