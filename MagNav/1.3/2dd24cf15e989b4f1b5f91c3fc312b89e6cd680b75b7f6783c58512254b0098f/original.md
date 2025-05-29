```
FILTres{T2 <: AbstractFloat}
```

Filter results struct.

| **Field** | **Type**      | **Description**                            |
|:--------- |:------------- |:------------------------------------------ |
| `x`       | Matrix{`T2`}  | filtered states, i.e., E(x*t   y*1,..,y_t) |
| `P`       | Array{`T2,3`} | non-linear covariance matrix               |
| `r`       | Matrix{`T2`}  | measurement residuals [nT]                 |
| `c`       | `Bool`        | if true, filter converged                  |
