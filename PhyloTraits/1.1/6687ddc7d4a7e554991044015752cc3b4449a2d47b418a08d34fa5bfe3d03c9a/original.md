```
ParamsBM <: ParamsProcess
```

Type for a BM process on a network. Fields are `mu` (expectation), `sigma2` (variance), `randomRoot` (whether the root is random, default to `false`), and `varRoot` (if the root is random, the variance of the root, default to `NaN`).
