```
prob_dde_DDETST_F3
```

Delay differential equation

$$
u'(t) = \exp(-u(t)) + L_3 \left[\sin(u'(\alpha(t))) - \sin\left(\frac{1}{3 + \alpha(t)}\right)\right]
$$

for $t \in [0, 10]$ with history function $\phi(0) = \log 3$ and $\phi'(0) = 1 / 3$, where $\alpha(t) = 0.5 t (1 - \cos(2 \pi t))$ and $L_3 = 0.2$.

# Solution

The analytical solution for $t \in [0, 10]$ is

$$
u(t) = \log(t + 3).
$$
