```
exp_underapproximation(A::IntervalMatrix{T}, t, p) where {T}
```

Underapproximation of the exponential of an interval matrix, `exp(A*t)`, using a truncated Taylor series expansion.

### Input

  * `A` – interval matrix
  * `t` – exponentiation factor
  * `p` – order of the approximation

### Output

An underapproximation of `exp(A*t)`, i.e. an interval matrix `M = (m_{ij})` such that `m_{ij} ⊆ [exp(A*t)]_{ij}`.

### Algorithm

See Theorem 2 in *Reachability Analysis of Linear Systems with Uncertain Parameters and Inputs* by M. Althoff, O. Stursberg, M. Buss.
