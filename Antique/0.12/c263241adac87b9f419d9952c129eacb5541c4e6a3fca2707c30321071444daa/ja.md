## モデル

このモデルは時間非依存のシュレーディンガー方程式で記述されます

$$
  \hat{H} \psi(x) = E \psi(x),
$$

およびハミルトニアン

$$
  \hat{H} =
  - \frac{\hbar^2}{2 m} \frac{\mathrm{d}^2}{\mathrm{d}x ^2}
  - \frac{\hbar^2}{m x_0^2} \frac{\lambda(\lambda+1)}{2} \frac{1}{\mathrm{cosh}^2(x/x_0)}.
$$

無次元変数を導入すると

$$
  x^\ast \equiv x/x_0,\qquad E^\ast \equiv \frac{\hbar^2}{m x_0^2} E
$$

シュレーディンガー方程式は次のように簡略化されます

$$
  \hat{H}^\ast \psi(x^\ast) = E^\ast \psi(x^\ast),
$$

ここで

$$
  \hat{H}^\ast = - \frac{1}{2} \frac{\mathrm{d}^2}{\mathrm{d}{x^\ast}^2} - \frac{\lambda(\lambda+1)}{2} \frac{1}{\mathrm{cosh}^2(x^\ast)}.
$$

パラメータは次の構造体内で指定されます：

```
PT = PoschlTeller(λ=1, m=1.0, ℏ=1.0, x₀=1.0)
```

$$
\lambda
$$

はポテンシャルの強さを決定します。現在、$\lambda$ の整数値のみがサポートされています。

## 参考文献

  * [G. Pöschl, E. Teller, *Zeitschrift für Physik*, **83** (3–4), 143 (1933)](https://doi.org/10.1007%2FBF01331132): より一般的な定義は (2a), (2b) または (11) として示されています。
  * [S. Flügge, Practical Quantum Mechanics (Springer Berlin Heidelberg, 1999)](https://doi.org/10.1007/978-3-642-61995-3) [p.94 問題 39. 修正ポシュル・テラー型のポテンシャルホール](https://archive.org/details/PracticalQuantumMechanicsS.Flgge/page/n111/mode/2up)。
