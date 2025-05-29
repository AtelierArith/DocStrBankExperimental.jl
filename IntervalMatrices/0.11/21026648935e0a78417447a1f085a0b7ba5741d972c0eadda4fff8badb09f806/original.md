```
sample(A::IntervalMatrix{T}; rng::AbstractRNG=GLOBAL_RNG) where {T}
```

Return a sample of the given random interval matrix.

### Input

  * `A`   – interval matrix
  * `m`   – (optional, default: `2`) number of rows
  * `n`   – (optional, default: `2`) number of columns
  * `rng` – (optional, default: `GLOBAL_RNG`) random-number generator

### Output

An interval matrix of size $m × n$ whose coefficients are normally-distributed intervals of type `N` with mean `0` and standard deviation `1`.
