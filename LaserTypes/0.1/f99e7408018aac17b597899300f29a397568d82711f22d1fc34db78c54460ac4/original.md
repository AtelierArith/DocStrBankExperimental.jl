```
Fμν(x, laser)
```

Compute [the electromagnetic tensor](https://en.wikipedia.org/wiki/Electromagnetic_tensor) $F$ in covarinat matrix form at the spacetime 4-vector specified by `x`. The $x = (x^0 ≡ ct, x^1, x^2, x^3)$ convention is used.

$$
F^{μν} =
\left[\begin{array}{cccc}
    0   &  -E_x / c  & -E_y / c & -E_z / c \\
E_x / c &       0    &   -B_z   &    B_y   \\
E_y / c &      B_z   &     0    &   -B_x   \\
E_z / c &     -B_y   &    B_z   &     0
\end{array}\right]
$$
