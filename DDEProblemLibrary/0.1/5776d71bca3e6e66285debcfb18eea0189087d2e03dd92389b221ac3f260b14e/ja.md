```
prob_dde_DDETST_G1
```

遅延微分方程

$$
u'(t) = - u'(t - u(t)^2 / 4)
$$

$$
t \in [0, 1]
$$

の範囲で、歴史関数は $\phi(t) = 1 - t$ （$t \leq 0$ の場合）および $\phi'(t) = -1$ （$t < 0$ の場合）です。

# 解

$$
t \in [0, 1]
$$

の範囲での解析解は

$$
u(t) = t + 1.
$$

# 参考文献

El'sgol'ts, L. E. and Norkin, S. B. (1973). Introduction to the Theory and Application of Differential Equations with Deviating Arguments, Academic Press, New York, p. 44.
