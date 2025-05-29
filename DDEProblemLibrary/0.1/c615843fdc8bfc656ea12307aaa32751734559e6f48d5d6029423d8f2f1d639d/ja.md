```
prob_dde_RADAR5_robertson
```

遅延微分方程モデルは、化学反応の定常状態解を与えます。

$$
  u_1'(t) = - a u_1(t) + b u_2(t - \tau) u_3(t), 
$$

$$
  u_2'(t) = a u_1(t) - b u_2(t - \tau) u_3(t) - c u_2(t)^2, 
$$

$$
  u_3'(t) = c u_2(t)^2,
$$

$$
t \in [0, 10e10]
$$

の範囲で、履歴関数は $\phi_1(0) = 1$, $\phi_2(t) = 0$ for $t \in [-\tau, 0]$, そして $\phi_3(0) = 0$ です。ここで、$a = 0.04$, $b = 10_000$, $c = 3e7$, および $\tau = 0.01$ です。

# 参考文献

Guglielmi, N. and Hairer, E. (2001). Implementing Radau IIA methods for stiff delay differential equations, Computing (67), pp. 1-12.
