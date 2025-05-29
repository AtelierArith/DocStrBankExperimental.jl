```
root_zz()
```

Return the `DiagonalOperator` that, when applied twice in sequence, applies rotations about the $Z$ axes of $-\frac{\pi}{2}$ to the first qubit and $\frac{\pi}{2}$ to the second one.

The `DiagonalOperator` is defined as:

$$
R_{ZZ} = \begin{bmatrix}
    1-i & 0 & 0 & 0 \\
    0 & 1+i & 0 & 0 \\
    0 & 0 & 1+i & 0 \\
    0 & 0 & 0 & 1-i \\
\end{bmatrix}.
$$
