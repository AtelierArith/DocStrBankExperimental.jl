## モデル

このモデルは時間非依存のシュレーディンガー方程式で記述されます。

$$
  \hat{H} \psi(r) = E \psi(r),
$$

およびハミルトニアン

$$
  \hat{H} = - \frac{\hbar^2}{2\mu} \frac{\mathrm{d}^2}{\mathrm{d}r ^2} + D_\mathrm{e} \left( \mathrm{e}^{-2a(r-r_e)} - 2\mathrm{e}^{-a(r-r_e)} \right),
$$

ここで、$a = \sqrt{\frac{k}{2Dₑ}}$ が定義されています。パラメータは以下の構造体で指定されます。

```
MP = MorsePotential(rₑ=2.0, Dₑ=0.1, k=0.1, µ=918.1, ℏ=1.0)
```

$$
r_\mathrm{e}
$$

は平衡結合距離、$D_\mathrm{e}$ は井戸の深さ、$k$ は力定数、$\mu$ は縮小質量、$\hbar$ は縮小プランク定数（ディラック定数）です。

## 参考文献

  * [P. M. Morse, *Phys. Rev.*, **34**, 57 (1929)](https://doi.org/10.1103/PhysRev.34.57)
  * [J. P. Dahl, M. Springborg, *J. Chem. Phys.*, **88**, 4535 (1988). (62), (63)](https://doi.org/10.1063/1.453761)
  * [W. K. Shao, Y. He, J. Pan, *J. Nonlinear Sci. Appl.*, **9**, 5, 3388 (2016). (1.6)](http://dx.doi.org/10.22436/jnsa.009.05.124)
  * 数学関数のデジタルライブラリ (DLMF) [18.3 Table1](https://dlmf.nist.gov/18.3#T1), [18.5 Table1](https://dlmf.nist.gov/18.5#T1), [18.5.12](https://dlmf.nist.gov/18.5#E12), [18.5.17_5](https://dlmf.nist.gov/18.5#E17_5)
