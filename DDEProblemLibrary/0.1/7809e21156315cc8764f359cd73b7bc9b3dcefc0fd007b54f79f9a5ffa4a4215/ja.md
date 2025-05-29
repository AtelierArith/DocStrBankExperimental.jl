```
prob_dde_DDETST_H1
```

遅延微分方程

$$
u'(t) = - \frac{4 t u(t)^2}{4 + \log(\cos(2t))^2} + \tan(2t) + 0.5 \arctan\left(u'\left(\frac{t u(t)^2}{1 + u(t)^2}\right)\right)
$$

$$
t \in [0, 0.225 \pi]
$$

の範囲で、履歴関数は $\phi(0) = 0$ および $\phi'(0) = 0$ です。

# 解

$$
t \in [0, 0.225 \pi]
$$

の範囲における解析解は

$$
u(t) = - \log(\cos(2t)) / 2.
$$

# 参考文献

Castleton, R. N. and Grimm, L. J. (1973). A first order method for differential equations of neutral type, Math. Comput. (27), pp. 571-577.
