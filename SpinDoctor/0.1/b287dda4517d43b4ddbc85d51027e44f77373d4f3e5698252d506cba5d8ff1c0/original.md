```
integral(f, t = echotime(f))
```

Integral of time profile `f` between `0` and `t`. Unless specified, the echotime is used as the upper integral limit.

For the `PGSE`, `SinOGSE`, `CosOGSE` and `DoublePGSE` sequences, analytical expressions are available. Otherwise a numerical integral is computed.
