```
prob_dde_DDETST_F2
```

遅延微分方程

$$
u'(t) = u'(2t - 0.5)
$$

$$
t \in [0.25, 0.499]
$$

の範囲で、履歴関数は $\phi(t) = \exp(-t^2)$ であり、$t \leq 0.25$ の場合は $\phi'(t) = -2t \exp(-t^2)$ です。

# 解

$$
t \in [0.25, 0.499]
$$

の範囲における解析解は

$$
u(t) = u_i(t) = \exp(-4^i t^2 + B_i t + C_i) / 2^i + K_i
$$

であり、$t \in [x_i, x_{i + 1}]$ の場合、ここで

$$
x_i = (1 - 2^{-i}) / 2, 
$$

$$
B_i = 2 (4^{i-1} + B_{i-1}), 
$$

$$
C_i = - 4^{i-2} - B_{i-1} / 2 + C_{i-1}, 
$$

$$
K_i = - \exp(-4^i x_i^2 + B_i x_i + C_i) / 2^i + u_{i-1}(x_i),
$$

そして $B_0 = C_0 = K_0 = 0$ です。

# 参考文献

Neves, K. W. and Thompson, S. (1992). Solution of systems of functional differential equations with state dependent delays, Technical Report TR-92-009, Computer Science, Radford University.
