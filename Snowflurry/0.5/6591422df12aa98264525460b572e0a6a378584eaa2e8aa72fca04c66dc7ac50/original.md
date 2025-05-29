```
rotation(theta, phi)
```

Return the `Operator` that applies a rotation `theta` about the axis $\vec{n}=\cos(\phi)~X+\sin(\phi)~Y$.

The `Operator` is defined as:

$$
R(\theta, \phi) = \begin{bmatrix}
    \mathrm{cos}\left(\frac{\theta}{2}\right) &
        -i e^{-i\phi} \mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
    -i e^{i\phi} \mathrm{sin}\left(\frac{\theta}{2}\right) &
        \mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
