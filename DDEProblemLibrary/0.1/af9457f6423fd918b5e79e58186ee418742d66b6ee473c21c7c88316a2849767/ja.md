```
prob_dde_DDETST_C4
```

造血の遅延微分方程式モデルで、[`prob_dde_DDETST_C3`](@ref)と同じ遅延微分方程式によって与えられます。

$$
u_1'(t) = \hat{s}_0 u_2(t - T_1) - \gamma u_1(t) - Q,
$$

$$
u_2'(t) = f(u_1(t)) - k u_2(t),
$$

$$
u_3'(t) = 1 - \frac{Q \exp(\gamma u_3(t))}{\hat{s}_0 u_2(t - T_1 - u_3(t))},
$$

$$
t \in [0, 100]
$$

の範囲で、履歴関数は $\phi_1(0) = 3.5$, $\phi_3(0) = 50$, そして $t \leq 0$ の場合に $\phi_2(t) = 10$ であり、$f(y) = a / (1 + K y^r)$, $\hat{s}_0 = 0.00372$, $T_1 = 3$, $\gamma = 0.1$, $Q = 0.00178$, $k = 6.65$, $a = 15600$, $K = 0.0382$, $r = 6.96$ です。

# 参考文献

Mahaffy, J. M., Belair, J. and Mackey, M. C. (1996). Hematopoietic model with moving boundary condition and state dependent delay, Private communication.
