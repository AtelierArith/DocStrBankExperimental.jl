```
prob_dde_DDETST_F3
```

遅延微分方程

$$
u'(t) = \exp(-u(t)) + L_3 \left[\sin(u'(\alpha(t))) - \sin\left(\frac{1}{3 + \alpha(t)}\right)\right]
$$

$$
t \in [0, 10]
$$

の範囲で、履歴関数は $\phi(0) = \log 3$ および $\phi'(0) = 1 / 3$ であり、$\alpha(t) = 0.5 t (1 - \cos(2 \pi t))$ および $L_3 = 0.2$ です。

# 解

$$
t \in [0, 10]
$$

の範囲での解析解は

$$
u(t) = \log(t + 3).
$$
