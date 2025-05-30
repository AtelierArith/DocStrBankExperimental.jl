```
gamma_inc_inv_psmall(a, logr)
```

`p`が小さいときの初期近似値`x0`を計算します。ここでは、論文の式(2.20)の級数を反転し、反転問題を次のように書きます：

$$
x = r\left[1 + a\sum_{k=1}^{\infty}\frac{(-x)^{n}}{(a+n)n!}\right]^{-1/a},
$$

ここで、$r = (p\Gamma(1+a))^{1/a}$ この関係を反転することで、$x = r + \sum_{k=2}^{\infty} c_{k} r^{k}$を得ます。
