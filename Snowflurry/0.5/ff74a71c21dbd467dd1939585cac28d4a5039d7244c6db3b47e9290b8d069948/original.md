```
rotation_x(theta)
```

Return the `Operator` which applies a rotation `theta` about the $X$ axis.

The `Operator` is defined as:

$$
R_x(\theta) = \begin{bmatrix}
\mathrm{cos}\left(\frac{\theta}{2}\right) &
    -i\mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
-i\mathrm{sin}\left(\frac{\theta}{2}\right) &
    \mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
