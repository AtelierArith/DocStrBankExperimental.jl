```
universal(theta, phi, lambda)
```

Return the `Operator` which performs a rotation about the angles `theta`, `phi`, and `lambda`. See Theorem 4.1 in [Quantum Computation and Quantum Information by Nielsen and Chuang](https://en.wikipedia.org/wiki/Quantum_Computation_and_Quantum_Information).

The `Operator` is defined as:

$$
U(\theta, \phi, \lambda) = \begin{bmatrix}
    \mathrm{cos}\left(\frac{\theta}{2}\right) &
        -e^{i\lambda}\mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
    e^{i\phi}\mathrm{sin}\left(\frac{\theta}{2}\right) &
        e^{i\left(\phi+\lambda\right)}\mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
