```julia
corr_cholesky_factor(n)

```

Transform into a Cholesky factor of a correlation matrix.

If the argument is a (positive) integer `n`, it determines the size of the output `n × n`, resulting in a `Matrix`.

If the argument is `SMatrix{N,N}`, an `SMatrix` is produced.
