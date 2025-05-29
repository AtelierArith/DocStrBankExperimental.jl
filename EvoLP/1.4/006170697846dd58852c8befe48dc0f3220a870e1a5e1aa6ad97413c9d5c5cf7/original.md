```
ackley(x; a=20, b=0.2, c=2π)
```

**Ackley's** benchmark function. Global minimum is at the origin, with value of 0. Parameters are typically $a=20$, $b=0.2$, and $c=2\pi$.

$$
f(x) = -a \exp\left(-b\sqrt{\frac{1}{d} \sum_{i=1}^d x_i^2}\right)
- \exp\left(\frac{1}{d} \sum_{i=1}{d} \cos (cx_i) \right) + a + \exp(1)
$$
