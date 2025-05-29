```
exp_overapproximation(A::IntervalMatrix{T}, t, p)
```

Overapproximation of the exponential of an interval matrix, `exp(A*t)`, using a truncated Taylor series.

### Input

  * `A` – interval matrix
  * `t` – exponentiation factor
  * `p` – order of the approximation

### Output

A matrix enclosure of `exp(A*t)`, i.e. an interval matrix `M = (m_{ij})` such that `[exp(A*t)]_{ij} ⊆ m_{ij}`.

### Algorithm

See Theorem 1 in *Reachability Analysis of Linear Systems with Uncertain Parameters and Inputs* by M. Althoff, O. Stursberg, M. Buss.
