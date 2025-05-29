```
static_gain_compensation(l::LQGProblem, L = lqr(l))
static_gain_compensation(A, B, C, D, L)
```

$$
L_r
$$

を見つけるために

```
dcgain(closedloop(G)*Lr) ≈ I
```
