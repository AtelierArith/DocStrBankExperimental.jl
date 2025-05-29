```
info.η
AMORS.effective_hyperparameter(info::AMORS.Info)
AMORS.effective_hyperparameter(μ, q, ν, r)
```

yield the value of the effective hyper-parameter in AMORS algorithm:

```
η = ((r/q)^qp + (q/r)^rp)*(μ^rp)*(ν^qp)
```

with:

```
qp = q/(q + r)
rp = r/(q + r)
```

and with `q = deg(J)` and `r = deg(K)` the homogeneous degrees of the functions `J(x)` and `K(y)` and `μ > 0` and `ν > 0` their respective multipliers. All required arguments may be provided by AMORS algorithm state `info`.
