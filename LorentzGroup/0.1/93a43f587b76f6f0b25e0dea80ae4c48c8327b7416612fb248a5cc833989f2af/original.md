```
lorentzfactor(v::Number)
```

Compute the Lorentz factor $\gamma$ for (coordinate) speed $v$, defined as

$$
\gamma^{-2} = |1 - v^2|
$$

This does not error but gives a correct result for tachyonic velocities $v > 1$, which is relevant when normalizing spacelike vectors.
