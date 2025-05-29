```
phase_shift(phi)
```

Return the `DiagonalOperator` that applies a phase shift `phi`.

The `DiagonalOperator` is defined as:

$$
P(\phi) = \begin{bmatrix}
    1 & 0 \\[0.5em]
    0 & e^{i\phi}
\end{bmatrix}.
$$
