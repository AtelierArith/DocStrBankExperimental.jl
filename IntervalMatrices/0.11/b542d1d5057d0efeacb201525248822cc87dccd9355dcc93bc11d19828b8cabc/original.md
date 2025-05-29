```
rand(::Type{IntervalMatrix}, m::Int=2, [n]::Int=m;
     N=Float64, rng::AbstractRNG=GLOBAL_RNG)
```

Return a random interval matrix of the given size and numeric type.

### Input

  * `IntervalMatrix` – type, used for dispatch
  * `m`              – (optional, default: `2`) number of rows
  * `n`              – (optional, default: `m`) number of columns
  * `rng`            – (optional, default: `GLOBAL_RNG`) random-number generator

### Output

An interval matrix of size $m × n$ whose coefficients are normally-distributed intervals of type `N` with mean `0` and standard deviation `1`.

### Notes

If this function is called with only one argument, it creates a square matrix, because the number of columns defaults to the number of rows.
