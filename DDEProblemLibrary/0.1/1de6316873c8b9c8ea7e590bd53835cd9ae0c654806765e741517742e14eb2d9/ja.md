```
prob_dde_DDETST_H2
```

遅延微分方程式

$$
u'(t) = \cos(t) (1 + u(t u(t)^2)) + L_3 u(t) u'(t u(t)^2) + (1 - L_3) \sin(t) \cos(t \sin(t)^2) - \sin(t + t \sin(t)^2)
$$

$$
t \in [0, \pi]
$$

の範囲で、履歴関数は $\phi(0) = 0$ および $\phi'(0) = 1$ であり、$L_3 = 0.1$ です。

# 解

$$
t \in [0, \pi]
$$

の範囲での解析解は

$$
u(t) = \sin(t).
$$

# 参考文献

Hayashi, H. (1996). Numerical solution of retarded and neutral delay differential equations using continuous Runge-Kutta methods, PhD thesis, Department of Computer Science, University of Toronto, Toronto, Canada.
