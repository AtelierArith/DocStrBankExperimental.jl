## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(\pmb{r}) = E \psi(\pmb{r}),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2\mu} \nabla^2 + \frac{1}{2} k r^2.
$$

Parameters are specified with the following struct:

```
SO = SphericalOscillator(k=1.0, μ=1.0, ℏ=1.0)
```

$k$ is the force constant, $μ$ is the mass of particle and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

  * [S. Flügge, *Practical Quantum Mechanics* (Springer Berlin Heidelberg, 1999)](https://doi.org/10.1007/978-3-642-61995-3) [p.166, Problem 65. Spherical oscillator](https://archive.org/details/PracticalQuantumMechanicsS.Flgge/page/n183/mode/2up).
  * [Quantum harmonic oscillator](https://beit.tech/blog/quantum-harmonic-oscillator.html)
  * [UCSD Physics 130, Quantum Physics](https://quantummechanics.ucsd.edu/ph130a/130_notes/node244.html)
