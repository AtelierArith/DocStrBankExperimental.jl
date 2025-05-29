```
prob_dde_DDETST_B2
```

遅延微分方程

$$
u'(t) = - 1 - u(t) + 2 [u(t / 2) < 0]
$$

$$
t \in [0, 2 \log 66]
$$

の範囲で、履歴関数は $\phi(0) = 1$ です。

# 解

$$
t \in [0, 2 \log 66]
$$

の範囲における解析解は

$$
u(t) = \begin{cases}
  2 \exp(-t) - 1 & \text{if } t \in [0, 2 \log 2], \\
  1 - 6 \exp(-t) & \text{if  } t \in (2 \log 2, 2 \log 6], \\
  66 \exp(-t) - 1 & \text{if } t \in (2 \log 6, 2 \log 66].
\end{cases}
$$

# 参考文献

Neves, K. W. and Thompson, S. (1992). Solution of systems of functional differential equations with state dependent delays, Technical Report TR-92-009, Computer Science, Radford University.
