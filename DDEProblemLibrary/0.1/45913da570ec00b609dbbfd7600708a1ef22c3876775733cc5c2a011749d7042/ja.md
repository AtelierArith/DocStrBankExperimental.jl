```
prob_dde_DDETST_D2
```

抗原抗体動態の遅延微分方程式モデルで、フェーディングメモリを持ち、次のように表されます。

$$
u_1'(t) = - r_1 u_1(t) u_2(t) + r_2 u_3(t), 
$$

$$
u_2'(t) = - r_1 u_1(t) u_2(t) + \alpha r_1 u_1(t - u_4(t)) u_2(t - u_4(t)),
$$

$$
u_3'(t) = r_1 u_1(t) u_2(t) - r_2 u_3(t), 
$$

$$
u_4'(t) = 1 + \frac{3 \delta - u_1(t) u_2(t) - u_3(t)}{u_1(t - u_4(t)) u_2(t - u_4(t)) + u_3(t - u_4(t))} \exp(\delta u_4(t)),
$$

$$
t \in [0, 40]
$$

の範囲で、履歴関数は次のようになります。

$$
\phi_1(t) = 5, 
$$

$$
\phi_2(t) = 0.1, 
$$

$$
\phi_3(t) = 0, 
$$

$$
\phi_4(t) = 0,
$$

$$
t \leq 0
$$

の場合、ここで $r_1 = 0.02$, $r_2 = 0.005$, $\alpha = 3$, および $\delta = 0.01$ です。

# 参考文献

Gatica, J. and Waltman, P. (1982). A threshold model of antigen antibody dynamics with fading memory, in Lakshmikantham (ed.), Nonlinear phenomena in mathematical science, Academic Press, New York, pp. 425-439.
