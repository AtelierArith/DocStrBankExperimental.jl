## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(r) = E \psi(r),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2\mu} \frac{\mathrm{d}^2}{\mathrm{d}r ^2} + D_\mathrm{e} \left( \mathrm{e}^{-2a(r-r_e)} - 2\mathrm{e}^{-a(r-r_e)} \right),
$$

where $a = \sqrt{\frac{k}{2Dₑ}}$ is defined. Parameters are specified with the following struct:

```
MP = MorsePotential(rₑ=2.0, Dₑ=0.1, k=0.1, µ=918.1, ℏ=1.0)
```

$r_\mathrm{e}$ is the equilibrium bond distance, $D_\mathrm{e}$ is the the well depth , $k$ is the force constant, $\mu$ is the reduced mass and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

  * [P. M. Morse, *Phys. Rev.*, **34**, 57 (1929)](https://doi.org/10.1103/PhysRev.34.57)
  * [J. P. Dahl, M. Springborg, *J. Chem. Phys.*, **88**, 4535 (1988). (62), (63)](https://doi.org/10.1063/1.453761)
  * [W. K. Shao, Y. He, J. Pan, *J. Nonlinear Sci. Appl.*, **9**, 5, 3388 (2016). (1.6)](http://dx.doi.org/10.22436/jnsa.009.05.124)
  * The Digital Library of Mathematical Functions (DLMF) [18.3 Table1](https://dlmf.nist.gov/18.3#T1), [18.5 Table1](https://dlmf.nist.gov/18.5#T1), [18.5.12](https://dlmf.nist.gov/18.5#E12), [18.5.17_5](https://dlmf.nist.gov/18.5#E17_5)
