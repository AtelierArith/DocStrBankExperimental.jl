```
prob_dde_DDETST_A1
```

血液生成の遅延微分方程式モデルは、次のように与えられます。

$$
u'(t) = \frac{0.2 u(t - 14)}{1 + u(t - 14)^{10}} - 0.1 u(t)
$$

$$
t \in [0, 500]
$$

の範囲で、履歴関数は $\phi(t) = 0.5$ であり、$t \leq 0$ の場合です。

# 参考文献

Mackey, M. C. and Glass, L. (1977). Oscillation and chaos in physiological control systems, Science (197), pp. 287-289.
