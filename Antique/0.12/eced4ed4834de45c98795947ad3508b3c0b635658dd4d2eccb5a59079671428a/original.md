## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(x) = E \psi(x),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2m} \frac{\mathrm{d}^2}{\mathrm{d}x ^2} - \alpha \delta(x).
$$

Parameters are specified with the following struct:

```
DP = DeltaPotential(α=1.0, m=1.0, ℏ=1.0)
```

$\alpha$ is the potential strength, $m$ is the mass of particle and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

  * [D. J. Griffiths, D. F. Schroeter, *Introduction to Quantum Mechanics* **Third Edition** (Cambridge University Press, 2018)](https://doi.org/10.1017/9781316995433) p.63, 2.5.2 The Delta-Function Well
  * [UCSD Physics 130, Quantum Physics](https://quantummechanics.ucsd.edu/ph130a/130_notes/node154.html)
