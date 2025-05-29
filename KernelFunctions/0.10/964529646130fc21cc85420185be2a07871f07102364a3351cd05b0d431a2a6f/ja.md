```
FBMKernel(; h::Real=0.5)
```

ハースト指数 `h` を持つ分数ブラウン運動カーネル。

# 定義

入力 $x, x' \in \mathbb{R}^d$ に対して、ハースト指数 [Hurst index](https://en.wikipedia.org/wiki/Hurst_exponent#Generalized_exponent) $h \in [0,1]$ を持つ分数ブラウン運動カーネルは次のように定義されます。

$$
k(x, x'; h) =  \frac{\|x\|_2^{2h} + \|x'\|_2^{2h} - \|x - x'\|^{2h}}{2}.
$$
