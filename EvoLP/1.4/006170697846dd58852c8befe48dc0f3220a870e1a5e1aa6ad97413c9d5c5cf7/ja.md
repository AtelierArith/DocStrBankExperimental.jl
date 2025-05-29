```
ackley(x; a=20, b=0.2, c=2π)
```

**アックレー**のベンチマーク関数。グローバルミニマムは原点にあり、その値は0です。パラメータは通常 $a=20$, $b=0.2$, および $c=2\pi$ です。

$$
f(x) = -a \exp\left(-b\sqrt{\frac{1}{d} \sum_{i=1}^d x_i^2}\right)
- \exp\left(\frac{1}{d} \sum_{i=1}{d} \cos (cx_i) \right) + a + \exp(1)
$$
