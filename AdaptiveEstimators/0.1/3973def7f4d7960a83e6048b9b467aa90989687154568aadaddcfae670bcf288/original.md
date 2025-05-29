```
LinearModel(ptype, n)
```

Linear scalar system model of specified order `n` and type `ptype`, such that:

```
y[t] = dot(p, x[t:-1:t-n+1]) + noise
```

for input `x`, output `y`, parameters `p` and time index `t`.
