## モデル

このモデルは時間非依存のシュレーディンガー方程式で記述されます

$$
  \hat{H} \psi(\pmb{r}) = E \psi(\pmb{r}),
$$

およびハミルトニアン

$$
  \hat{H} = - \frac{\hbar^2}{2\mu} \nabla^2 + \frac{1}{2} k r^2.
$$

パラメータは次の構造体で指定されます：

```
SO = SphericalOscillator(k=1.0, μ=1.0, ℏ=1.0)
```

$$
k
$$

は力定数、$μ$は粒子の質量、$\hbar$は縮小プランク定数（ディラック定数）です。

## 参考文献

  * [S. Flügge, *Practical Quantum Mechanics* (Springer Berlin Heidelberg, 1999)](https://doi.org/10.1007/978-3-642-61995-3) [p.166, 問題 65. 球面振動子](https://archive.org/details/PracticalQuantumMechanicsS.Flgge/page/n183/mode/2up).
  * [量子調和振動子](https://beit.tech/blog/quantum-harmonic-oscillator.html)
  * [UCSD 物理学 130, 量子物理学](https://quantummechanics.ucsd.edu/ph130a/130_notes/node244.html)
