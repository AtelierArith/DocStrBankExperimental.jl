```
static_gain_compensation(l::LQGProblem, L = lqr(l))
static_gain_compensation(A, B, C, D, L)
```

Find $L_r$ such that

```
dcgain(closedloop(G)*Lr) ≈ I
```
