```
prob_dde_DDETST_F1
```

遅延微分方程

$$
u'(t) = 2 \cos(2t) u(t / 2)^{2 \cos t} + \log(u'(t / 2)) - \log(2 \cos t) - \sin t
$$

のために $t \in [0, 1]$ で歴史関数 $\phi(0) = 1$ および $\phi'(0) = 2$。

# 解

$$
t \in [0, 1]
$$

のための解析解は

$$
u(t) = \exp(\sin(2t)).
$$

# 参考文献

Jackiewicz, Z. (1981). One step methods for the numerical solution of Volterra functional differential equations of neutral type, Applicable Anal. (12), pp. 1-11.
