```
prob_dde_DDETST_C2
```

遅延微分方程

$$
u_1'(t) = - 2 u_1(t - u_2(t)),
$$

$$
u_₂'(t) = \frac{|u_1(t - u_2(t))| - |u_1(t)|}{1 + |u_1(t - u_2(t))|},
$$

$ t \in [0, 40] $ の範囲で、履歴関数は

$$
\phi_1(t) = 1,
$$

$$
\phi_2(t) = 0.5,
$$

$ t \leq 0 $ の場合です。

# 参考文献

Paul, C. A. H. (1994). A test set of functional differential equations, Technical Report 249, The Department of Mathematics, The University of Manchester, Manchester, England.
