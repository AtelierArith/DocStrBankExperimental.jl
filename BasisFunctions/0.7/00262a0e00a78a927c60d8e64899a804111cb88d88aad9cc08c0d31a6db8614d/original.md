A generic orthogonal polynomial sequence is determined by its recurrence coefficients. The `GenericOPS` type stores the coefficients `A_n`, `B_n` and `C_n` from the recurrence relation in the following form:

```
p_{n+1}(x) = (A_n x + B_n) * p_n(x) - C_n * p_{n-1}(x).
p_{-1} = 0, p_0 = p0
```
