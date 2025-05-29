## Model

This model is described with the time-independent Schrödinger equation

$$
  \hat{H} \psi(\pmb{r}) = E \psi(\pmb{r}),
$$

and the Hamiltonian

$$
  \hat{H} = - \frac{\hbar^2}{2\mu} \nabla^2 - \frac{Z}{r/a_0} E_\mathrm{h},
$$

where $\mu=\left(\frac{1}{m_\mathrm{e}}+\frac{1}{m_\mathrm{p}}\right)^{-1}$ is the reduced mass of electron $\mathrm{e}$ and proton $\mathrm{p}$. $\mu = m_\mathrm{e}$ holds in the limit $m_\mathrm{p}\rightarrow\infty$. The potential includes only Coulomb interaction and it does not include fine or hyperfine interactions in this model. Parameters are specified with the following struct:

```
HA = HydrogenAtom(Z=1, mₑ=1.0, a₀=1.0, Eₕ=1.0, ℏ=1.0)
```

$Z$ is the atomic number, $m_\mathrm{e}$ is the electron mass, $a_0$ is the Bohr radius, $E_\mathrm{h}$ is the Hartree energy and $\hbar$ is the reduced Planck constant (Dirac's constant).

## References

Main:

  * *The Digital Library of Mathematical Functions* (DLMF), [18.3 Table1](https://dlmf.nist.gov/18.3#T1), [18.5 Table1](https://dlmf.nist.gov/18.5#T1), [18.5.16](https://dlmf.nist.gov/18.5#E16), [18.5.17](https://dlmf.nist.gov/18.5#E17)
  * *cpprefjp*, [assoc_legendre](https://cpprefjp.github.io/reference/cmath/assoc_legendre.html), [assoc_laguerre](https://cpprefjp.github.io/reference/cmath/assoc_laguerre.html)
  * A. Messiah, *Quanfum Mechanics* **VOLUME Ⅰ** (North-Holland Publishing Company, 1961), p.412 (XI.3), p.419 (XI.18) (XI.18a) (XI.18b), p.483 (B.12), p.493 (B.71) (B.72), p.494 (B.81), p495 (B.93)

Supplemental:

  * cpprefjp, [legendre](https://cpprefjp.github.io/reference/cmath/legendre.html), [assoc_legendre](https://cpprefjp.github.io/reference/cmath/assoc_legendre.html), [laguerre](https://cpprefjp.github.io/reference/cmath/laguerre.html), [assoc_laguerre](https://cpprefjp.github.io/reference/cmath/assoc_laguerre.html)
  * The Digital Library of Mathematical Functions (DLMF), [18.3 Table1](https://dlmf.nist.gov/18.3#T1), [18.5 Table1](https://dlmf.nist.gov/18.5#T1), [18.5.16](https://dlmf.nist.gov/18.5#E16), [18.5.17](https://dlmf.nist.gov/18.5#E17), [18.5.12](https://dlmf.nist.gov/18.5#E12)
  * L. D. Landau, E. M. Lifshitz, Quantum Mechanics (Pergamon Press, 1965), [p.598 (c.1)](https://archive.org/details/ost-physics-landaulifshitz-quantummechanics/page/n611/mode/2up), [p.598 (c.4)](https://archive.org/details/ost-physics-landaulifshitz-quantummechanics/page/n611/mode/2up), [p.603 (d.13)](https://archive.org/details/ost-physics-landaulifshitz-quantummechanics/page/n615/mode/2up)
  * L. I. Schiff, Quantum Mechanics (McGraw-Hill Book Company, 1968), [p.79 (14.12)](https://archive.org/details/ost-physics-schiff-quantummechanics/page/n95/mode/1up), [p.93 (16.19)](https://archive.org/details/ost-physics-schiff-quantummechanics/page/n109/mode/1up)
  * A. Messiah, Quanfum Mechanics (Dover Publications, 1999), [p.493 (B.72)](https://archive.org/details/quantummechanics0000mess/page/491/mode/1up), [p.494 Table](https://archive.org/details/quantummechanics0000mess/page/494/mode/1up), [p.493 (B.72)](https://archive.org/details/quantummechanics0000mess/page/491/mode/1up), [p.483 (B.12)](https://archive.org/details/quantummechanics0000mess/page/483/mode/1up), [p.483 (B.12)](https://archive.org/details/quantummechanics0000mess/page/483/mode/1up)
  * W. Greiner, Quantum Mechanics: An Introduction Third Edition (Springer, 1994), [p.83 (4)](https://archive.org/details/quantummechanics0001grei_u4x0/page/83/mode/1up), [p.83 (5)](https://archive.org/details/quantummechanics0001grei_u4x0/page/83/mode/1up), [p.149 (21)](https://archive.org/details/quantummechanics0001grei_u4x0/page/149/mode/1up)
  * D. J. Griffiths, Introduction to Quantum Mechanics (Prentice Hall, 1995), [p.126 (4.28)](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/126/mode/1up), [p.96 Table3.1](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/95/mode/1up), [p.126 (4.27)](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/126/mode/1up), [p.139 (4.88)](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/139/mode/1up), [p.140 Table4.4](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/140/mode/1up), [p.139 (4.87)](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/139/mode/1up), [p.140 Table4.5](https://archive.org/details/griffiths-introduction-to-quantum-mechanics/page/140/mode/1up)
  * D. A. McQuarrie, J. D. Simon, Physical Chemistry: A Molecular Approach (University Science Books, 1997), [p.195 Table6.1](https://archive.org/details/McQuarrieSimonPhysicalChemistrySolutions/McQuarrie_Simon_Physical_Chemistry1997/page/n218/mode/1up), [p.196 (6.26)](https://archive.org/details/McQuarrieSimonPhysicalChemistrySolutions/McQuarrie_Simon_Physical_Chemistry1997/page/n219/mode/1up), [p.196 Table6.2](https://archive.org/details/McQuarrieSimonPhysicalChemistrySolutions/McQuarrie_Simon_Physical_Chemistry1997/page/n220/mode/1up), [p.207 Table6.4](https://archive.org/details/McQuarrieSimonPhysicalChemistrySolutions/McQuarrie_Simon_Physical_Chemistry1997/page/n230/mode/1up)
  * P. W. Atkins, J. De Paula, Atkins' Physical Chemistry, 8th edition (W. H. Freeman, 2008), [p.234](https://archive.org/details/atkinsphysicalch00pwat/page/324/mode/2up?q=Laguerre)
  * [J. J. Sakurai, J. Napolitano, Modern Quantum Mechanics Third Edition (Cambridge University Press, 2021)](https://doi.org/10.1017/9781108587280), p.245 Problem 3.30.b,
