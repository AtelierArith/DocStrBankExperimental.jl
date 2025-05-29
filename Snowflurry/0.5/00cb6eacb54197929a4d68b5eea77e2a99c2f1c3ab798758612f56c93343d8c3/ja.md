```
universal(theta, phi, lambda)
```

角度 `theta`、`phi`、および `lambda` に関する回転を行う `Operator` を返します。詳細は [Quantum Computation and Quantum Information by Nielsen and Chuang](https://en.wikipedia.org/wiki/Quantum_Computation_and_Quantum_Information) の定理 4.1 を参照してください。

`Operator` は次のように定義されます：

$$
U(\theta, \phi, \lambda) = \begin{bmatrix}
    \mathrm{cos}\left(\frac{\theta}{2}\right) &
        -e^{i\lambda}\mathrm{sin}\left(\frac{\theta}{2}\right) \\[0.5em]
    e^{i\phi}\mathrm{sin}\left(\frac{\theta}{2}\right) &
        e^{i\left(\phi+\lambda\right)}\mathrm{cos}\left(\frac{\theta}{2}\right)
\end{bmatrix}.
$$
