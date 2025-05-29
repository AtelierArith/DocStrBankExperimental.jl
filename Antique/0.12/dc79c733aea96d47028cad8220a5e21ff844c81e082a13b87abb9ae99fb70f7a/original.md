## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(x) = E \psi(x),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2m} \frac{\mathrm{d}^2}{\mathrm{d}x ^2} + \frac{1}{2} k x^2.
$$

Parameters are specified with the following struct:

```
HO = HarmonicOscillator(k=1.0, m=1.0, ℏ=1.0)
```

$k$ is the force constant, $m$ is the mass of particle and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

Main:

  * *The Digital Library of Mathematical Functions* (DLMF) [18.5.18](https://dlmf.nist.gov/18.5#E18)
  * *cpprefjp*, [hermite](https://cpprefjp.github.io/reference/cmath/hermite.html)
  * [D. J. Griffiths, D. F. Schroeter, *Introduction to Quantum Mechanics* **Third Edition** (Cambridge University Press, 2018)](https://doi.org/10.1017/9781316995433) p.48, 2.3.2 Analytic Method

Supplemental:

  * The Digital Library of Mathematical Functions (DLMF)                                                    [18.3 Table1](https://dlmf.nist.gov/18.3#T1), [18.5 Table1](https://dlmf.nist.gov/18.5#T1), [18.5.13](https://dlmf.nist.gov/18.5#E13), [18.5.18](https://dlmf.nist.gov/18.5#E18)
  * L. D. Landau, E. M. Lifshitz, Quantum Mechanics (Pergamon Press, 1965)                                  [p.595 (a.4), (a.6)](https://archive.org/details/ost-physics-landaulifshitz-quantummechanics/page/n607/mode/2up)
  * L. I. Schiff, Quantum Mechanics (McGraw-Hill Book Company, 1968)                                        [p.71 (13.12)](https://archive.org/details/ost-physics-schiff-quantummechanics/page/n87/mode/2up)
  * A. Messiah, Quanfum Mechanics (Dover Publications, 1999)                                                [p.491 (B.59)](https://archive.org/details/quantummechanics0000mess/page/491/mode/1up)
  * W. Greiner, Quantum Mechanics: An Introduction Third Edition (Springer, 1994)                           [p.152 (7.22)](https://archive.org/details/quantummechanics0001grei_u4x0/page/152/mode/1up)
  * D. J. Griffiths, Introduction to Quantum Mechanics (Prentice Hall, 1995)                                [p.41 Table 2.1](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/41/mode/1up), [p.43 (2.70)](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/43/mode/1up)
  * D. A. McQuarrie, J. D. Simon, Physical Chemistry: A Molecular Approach (University Science Books, 1997) [p.170 Table 5.2](https://archive.org/details/McQuarrieSimonPhysicalChemistrySolutions/McQuarrie_Simon_Physical_Chemistry1997/page/n193/mode/1up)
  * P. W. Atkins, J. De Paula, Atkins' Physical Chemistry, 8th edition (W. H. Freeman, 2008)                [p.293 Table 9.1](https://archive.org/details/atkinsphysicalch00pwat/page/292/mode/2up)
  * J. J. Sakurai, J. Napolitano, Modern Quantum Mechanics Third Edition (Cambridge University Press, 2021) [p.524 (B.29)](https://doi.org/10.1017/9781108587280)
