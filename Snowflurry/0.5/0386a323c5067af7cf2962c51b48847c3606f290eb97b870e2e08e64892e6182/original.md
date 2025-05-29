```
rotation_y(theta)
```

Return the `Operator` that applies a rotation `theta` about the $Y$ axis.

The `Operator` is defined as:

$$
R_y(\theta) = \begin{bmatrix}
\mathrm{cos}\left(\frac{\theta}{2}\right) &
    -\mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
\mathrm{sin}\left(\frac{\theta}{2}\right) &
    \mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
