## モデル

このモデルは時間非依存のシュレーディンガー方程式で記述されます。

$$
  \hat{H} \psi(\pmb{r}) = E \psi(\pmb{r}),
$$

およびハミルトニアン

$$
  \hat{H} = - \frac{\hbar^2}{2\mu} \nabla^2 + \frac{z_1 z_2}{r/a_0} E_\mathrm{h},
$$

ここで、$\mu=\left(\frac{1}{m_1}+\frac{1}{m_2}\right)^{-1}$は粒子1と粒子2の縮退質量です。ポテンシャルはクーロン相互作用のみを含み、このモデルでは精細または超精細相互作用は含まれていません。パラメータは次の構造体で指定されます。

```
CTB = CoulombTwoBody(z₁=-1, z₂=1, m₁=1.0, m₂=1.0, mₑ=1.0, a₀=1.0, Eₕ=1.0, ℏ=1.0)
```

$$
z₁
$$

は粒子1の電荷数、$z₂$は粒子2の電荷数、$m₁$は粒子1の質量、$m₂$は粒子2の質量、$m_\mathrm{e}$は電子の質量（$m₁$および$m₂$と同じ単位を使用します。水素原子の例では、$m_\mathrm{e}=9.1093837139\times10^{-31}\mathrm{kg}$、$m_1=9.1093837139\times10^{-31}\mathrm{kg}$および$m_2=1.67262192595\times10^{-27}\mathrm{kg}$を国際単位系で使用し、原子単位系では$~m_\mathrm{e}=1.0~m_\mathrm{e}$、$m_1=1.0~m_\mathrm{e}$および$m_2=1836.152673426~m_\mathrm{e}$を使用します)、$a_0$はボーア半径、$E_\mathrm{h}$はハートリーエネルギー、$\hbar$は縮退プランク定数（ディラック定数）です。

## 参考文献

  * *The Digital Library of Mathematical Functions* (DLMF), [18.3 Table1](https://dlmf.nist.gov/18.3#T1), [18.5 Table1](https://dlmf.nist.gov/18.5#T1), [18.5.16](https://dlmf.nist.gov/18.5#E16), [18.5.17](https://dlmf.nist.gov/18.5#E17)
  * *cpprefjp*, [assoc_legendre](https://cpprefjp.github.io/reference/cmath/assoc_legendre.html), [assoc_laguerre](https://cpprefjp.github.io/reference/cmath/assoc_laguerre.html)
  * A. Messiah, *Quanfum Mechanics* **VOLUME Ⅰ** (North-Holland Publishing Company, 1961), p.412 I. THE HYDROGEN ATOM
  * [D. J. Griffiths, D. F. Schroeter, *Introduction to Quantum Mechanics* **Third Edition** (Cambridge University Press, 2018)](https://doi.org/10.1017/9781316995433) p.143 4.2 THE HYDROGEN ATOM, p.200 Problem 5.1, p.200 Problem 5.2
  * [W. Greiner, *Quantum Mechanics: An Introduction* **Forth Edition** (Springer, 2001)](https://doi.org/10.1007/978-3-642-56826-8) p.217 The Hydrogen Atom, p.236 9.5 Spectrum of a Diatomic Molecule
