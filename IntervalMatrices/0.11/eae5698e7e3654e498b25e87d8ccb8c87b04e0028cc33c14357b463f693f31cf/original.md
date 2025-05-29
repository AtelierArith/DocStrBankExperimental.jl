```
opnorm(A::IntervalMatrix, p::Real=Inf)
```

The matrix norm of an interval matrix.

### Input

  * `A` – interval matrix
  * `p` – (optional, default: `Inf`) the class of `p`-norm

### Notes

The matrix $p$-norm of an interval matrix $A$ is defined as

$$
    ‖A‖_p := ‖\max(|\text{inf}(A)|, |\text{sup}(A)|)‖_p
$$

where $\max$ and $|·|$ are taken elementwise.
