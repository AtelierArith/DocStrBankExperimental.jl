```
prob_dde_DDETST_E2
```

ロジスティックガウス型捕食者-被捕食者システムの遅延微分方程式モデルは、次のように与えられます。

$$
u_1'(t) = u_1(t) (1 - u_1(t - \tau) - \rho u_1'(t - \tau)) - \frac{u_2(t) u_1(t)^2}{u_1(t)^2 + 1}, 
$$

$$
u_2'(t) = u_2(t) \left(\frac{u_1(t)^2}{u_1(t)^2 + 1} - \alpha\right),
$$

$$
t \in [0, 2]
$$

の範囲で、履歴関数は次のようになります。

$$
\phi_1(t) = 0.33 - t / 10, 
$$

$$
\phi_2(t) = 2.22 + t / 10,
$$

$$
t \leq 0
$$

の場合、ここで $\alpha = 0.1$, $\rho = 2.9$, および $\tau = 0.42$ です。

# 参考文献

Kuang, Y. (1991). On neutral delay logistics Gauss-type predator-prey systems, Dyn. Stab. Systems (6), pp. 173-189.
