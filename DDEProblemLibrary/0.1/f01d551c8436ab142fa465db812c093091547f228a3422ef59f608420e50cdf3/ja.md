```
prob_dde_DDETST_D1
```

遅延微分方程

$$
u_1'(t) = u_2(t), 
$$

$$
u_2'(t) = - u_2(\exp(1 - u_2(t))) u_2(t)^2 \exp(1 - u_2(t)),
$$

$$
t \in [0.1, 5]
$$

の範囲で、履歴関数は

$$
\phi_1(t) = \log t, 
$$

$$
\phi_2(t) = 1 / t,
$$

$$
t \in (0, 0.1]
$$

の範囲で。

# 解

$$
t \in [0.1, 5]
$$

の範囲における解析解は

$$
u_1(t) = \log t, 
$$

$$
u_2(t) = 1 / t.
$$

# 参考文献

Neves, K. W. (1975). Automatic integration of functional differential equations: An approach, ACM Trans. Math. Soft. (1), pp. 357-368.
