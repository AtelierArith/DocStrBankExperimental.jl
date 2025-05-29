```
bessels!(j, j′, y, y′, x)
```

Compute all spherical Bessel (regular: $j_n$) and Neumann (irregular: $y_n$) functions and their derivatives at `x` and store the results in the vectors `j`, `j′`, `y`, `y′`. If only the Bessel functions or the Neumann functions are of interest, the other pair of arrays can be substituted by `nothing`. However, it is not possible to compute only the functions but not the derivatives, since they are generated using the following recurrence relations:

$$
\begin{aligned}
g_{n-1} &= \frac{n+1}{x} g_n + g_n'\\
g'_{n-1} &= \frac{n-1}{x} g_{n-1} - g_n.
\end{aligned}
$$

These recurrence relations are employed in a *downward* fashion for the Bessel functions and an *upward* fashion for the Neumann functions.

It is assumed that all passed arrays are of the same lengths (not checked).
