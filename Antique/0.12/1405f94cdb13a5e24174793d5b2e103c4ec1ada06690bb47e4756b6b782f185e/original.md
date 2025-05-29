## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(\pmb{r}) = E \psi(\pmb{r}),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2\mu} \nabla^2 + \frac{z_1 z_2}{r/a_0} E_\mathrm{h},
$$

where $\mu=\left(\frac{1}{m_1}+\frac{1}{m_2}\right)^{-1}$ is the reduced mass of particle 1 and particle 2. The potential includes only Coulomb interaction and it does not include fine or hyperfine interactions in this model. Parameters are specified with the following struct:

```
CTB = CoulombTwoBody(z₁=-1, z₂=1, m₁=1.0, m₂=1.0, mₑ=1.0, a₀=1.0, Eₕ=1.0, ℏ=1.0)
```

$z₁$ is the charge number of particle 1,  $z₂$ is the charge number of particle 2,  $m₁$ is the mass of particle 1,  $m₂$ is the mass of particle 2, $m_\mathrm{e}$ is the electron mass (use the same unit as $m₁$ and $m₂$. For example of hydrogen atom, use $m_\mathrm{e}=9.1093837139\times10^{-31}\mathrm{kg}$, $m_1=9.1093837139\times10^{-31}\mathrm{kg}$ and $m_2=1.67262192595\times10^{-27}\mathrm{kg}$ in the IS unit system, use $~m_\mathrm{e}=1.0~m_\mathrm{e}$, $m_1=1.0~m_\mathrm{e}$ and $m_2=1836.152673426~m_\mathrm{e}$ in the atomic unit.), $a_0$ is the Bohr radius, $E_\mathrm{h}$ is the Hartree energy and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

  * *The Digital Library of Mathematical Functions* (DLMF), [18.3 Table1](https://dlmf.nist.gov/18.3#T1), [18.5 Table1](https://dlmf.nist.gov/18.5#T1), [18.5.16](https://dlmf.nist.gov/18.5#E16), [18.5.17](https://dlmf.nist.gov/18.5#E17)
  * *cpprefjp*, [assoc_legendre](https://cpprefjp.github.io/reference/cmath/assoc_legendre.html), [assoc_laguerre](https://cpprefjp.github.io/reference/cmath/assoc_laguerre.html)
  * A. Messiah, *Quanfum Mechanics* **VOLUME Ⅰ** (North-Holland Publishing Company, 1961), p.412 I. THE HYDROGEN ATOM
  * [D. J. Griffiths, D. F. Schroeter, *Introduction to Quantum Mechanics* **Third Edition** (Cambridge University Press, 2018)](https://doi.org/10.1017/9781316995433) p.143 4.2 THE HYDROGEN ATOM, p.200 Problem 5.1, p.200 Problem 5.2
  * [W. Greiner, *Quantum Mechanics: An Introduction* **Forth Edition** (Springer, 2001)](https://doi.org/10.1007/978-3-642-56826-8) p.217 The Hydrogen Atom, p.236 9.5 Spectrum of a Diatomic Molecule
