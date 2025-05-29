```
rydberg_corr([op=Op.n], reg) -> Matrix
```

Calculates the rydberg correlation matrix.

$$
\langle \text{op}_i \text{op}_j \rangle
$$

here `op` can be `Op.n`, `X` or `Y`.

# Arguments

  * `op`: the correlation function, default is `Op.n`.
  * `reg`: required, the register object.
