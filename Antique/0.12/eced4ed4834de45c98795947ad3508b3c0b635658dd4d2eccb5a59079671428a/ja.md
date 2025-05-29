## モデル

このモデルは時間非依存のシュレーディンガー方程式で記述されます

$$
  \hat{H} \psi(x) = E \psi(x),
$$

およびハミルトニアン

$$
  \hat{H} = - \frac{\hbar^2}{2m} \frac{\mathrm{d}^2}{\mathrm{d}x ^2} - \alpha \delta(x).
$$

パラメータは次の構造体で指定されます：

```
DP = DeltaPotential(α=1.0, m=1.0, ℏ=1.0)
```

$$
\alpha
$$

はポテンシャルの強さ、$m$ は粒子の質量、$\hbar$ は縮小プランク定数（ディラック定数）です。

## 参考文献

  * [D. J. Griffiths, D. F. Schroeter, *Introduction to Quantum Mechanics* **第三版** (ケンブリッジ大学出版, 2018)](https://doi.org/10.1017/9781316995433) p.63, 2.5.2 デルタ関数井戸
  * [UCSD 物理学 130,量子物理学](https://quantummechanics.ucsd.edu/ph130a/130_notes/node154.html)
