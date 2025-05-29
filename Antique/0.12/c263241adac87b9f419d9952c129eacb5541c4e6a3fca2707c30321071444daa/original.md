## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(x) = E \psi(x),
$$

and the Hamiltonian

$$
  \hat{H} =
  - \frac{\hbar^2}{2 m} \frac{\mathrm{d}^2}{\mathrm{d}x ^2}
  - \frac{\hbar^2}{m x_0^2} \frac{\lambda(\lambda+1)}{2} \frac{1}{\mathrm{cosh}^2(x/x_0)}.
$$

After introducing the dimensionless variables

$$
  x^\ast \equiv x/x_0,\qquad E^\ast \equiv \frac{\hbar^2}{m x_0^2} E
$$

the Schrödinger equation reduces to

$$
  \hat{H}^\ast \psi(x^\ast) = E^\ast \psi(x^\ast),
$$

with

$$
  \hat{H}^\ast = - \frac{1}{2} \frac{\mathrm{d}^2}{\mathrm{d}{x^\ast}^2} - \frac{\lambda(\lambda+1)}{2} \frac{1}{\mathrm{cosh}^2(x^\ast)}.
$$

Parameters are specified within the following struct:

```
PT = PoschlTeller(λ=1, m=1.0, ℏ=1.0, x₀=1.0)
```

$\lambda$ determines the potential strength. Currently only integer values for $\lambda$ are supported.

## References

  * [G. Pöschl, E. Teller, *Zeitschrift für Physik*, **83** (3–4), 143 (1933)](https://doi.org/10.1007%2FBF01331132): More general definitions are given as (2a), (2b) or (11).
  * [S. Flügge, Practical Quantum Mechanics (Springer Berlin Heidelberg, 1999)](https://doi.org/10.1007/978-3-642-61995-3) [p.94 Problem 39. Potential hole of modified Poschl-Teller type](https://archive.org/details/PracticalQuantumMechanicsS.Flgge/page/n111/mode/2up).
