```
prob_dde_DDETST_H1
```

Delay differential equation

$$
u'(t) = - \frac{4 t u(t)^2}{4 + \log(\cos(2t))^2} + \tan(2t) + 0.5 \arctan\left(u'\left(\frac{t u(t)^2}{1 + u(t)^2}\right)\right)
$$

for $t \in [0, 0.225 \pi]$ with history function $\phi(0) = 0$ and $\phi'(0) = 0$.

# Solution

The analytical solution for $t \in [0, 0.225 \pi]$ is

$$
u(t) = - \log(\cos(2t)) / 2.
$$

# References

Castleton, R. N. and Grimm, L. J. (1973). A first order method for differential equations of neutral type, Math. Comput. (27), pp. 571-577.
