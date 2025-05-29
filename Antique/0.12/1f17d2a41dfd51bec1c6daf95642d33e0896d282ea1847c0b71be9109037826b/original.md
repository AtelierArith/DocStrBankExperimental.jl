## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(x) = E \psi(x),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2m} \frac{\mathrm{d}^2}{\mathrm{d}x ^2} + V(x).
$$

Parameters are specified with the following struct:

```
IPW = InfinitePotentialWell(L=1.0, m=1.0, ℏ=1.0)
```

$L$ is the length of the box, $m$ is the mass of particle and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

  * [D. J. Griffiths, D. F. Schroeter, *Introduction to Quantum Mechanics* **Third Edition** (Cambridge University Press, 2018)](https://doi.org/10.1017/9781316995433) p.31, 2.2 THE INFINITE SQUARE WELL

## Proofs

  * [Eigen Functions & Eigen Values](https://ja.wolframalpha.com/input?i2d=true&i=D%5B%5C%2840%29Sqrt%5BDivide%5B2%2Ca%5D%5Dsin%5C%2840%29Divide%5Bn%CF%80x%2Ca%5D%5C%2841%29%5C%2841%29%2C%7Bx%2C2%7D%5D)
  * [Normalization](https://ja.wolframalpha.com/input?i=Integrate%5B%28%28Sqrt%5B2%2Fa%5Dsin%28%CF%80x%2Fa%29%29%29%5E2%2C+%7Bx%2C0%2Ca%7D%5D)
