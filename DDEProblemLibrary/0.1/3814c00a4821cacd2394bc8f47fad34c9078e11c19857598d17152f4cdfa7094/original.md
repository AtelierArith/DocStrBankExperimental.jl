```
prob_dde_DDETST_E1
```

Delay differential equation model of a food-limited population, given by

$$
u(t) = r u(t) (1 - u(t - 1) - c u'(t - 1))
$$

for $t \in [0, 40]$ with history function $\phi(t) = 2 + t$ for $t \leq 0$, where $r = \pi / \sqrt{3} + 1/20$ and $c = \sqrt{3} / (2 \pi) - 1 / 25$.

# References

Kuang, Y. and Feldstein, A. (1991). Boundedness of solutions of a nonlinear nonautonomous neutral delay equation, J. Math. Anal. Appl. (156), pp. 293-304.
