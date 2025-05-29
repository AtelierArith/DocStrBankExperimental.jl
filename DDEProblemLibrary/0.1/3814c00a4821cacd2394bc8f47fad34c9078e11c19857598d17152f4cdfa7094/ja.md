```
prob_dde_DDETST_E1
```

食物制限された集団の遅延微分方程式モデルは、次のように与えられます。

$$
u(t) = r u(t) (1 - u(t - 1) - c u'(t - 1))
$$

$$
t \in [0, 40]
$$

の範囲で、歴史関数は $\phi(t) = 2 + t$ であり、$t \leq 0$ の場合、$r = \pi / \sqrt{3} + 1/20$ および $c = \sqrt{3} / (2 \pi) - 1 / 25$ です。

# 参考文献

Kuang, Y. and Feldstein, A. (1991). Boundedness of solutions of a nonlinear nonautonomous neutral delay equation, J. Math. Anal. Appl. (156), pp. 293-304.
