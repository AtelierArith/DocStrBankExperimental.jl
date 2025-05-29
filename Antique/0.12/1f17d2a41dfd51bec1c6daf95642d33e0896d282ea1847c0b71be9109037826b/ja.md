## モデル

このモデルは時間に依存しないシュレーディンガー方程式で記述されます

$$
  \hat{H} \psi(x) = E \psi(x),
$$

およびハミルトニアン

$$
  \hat{H} = - \frac{\hbar^2}{2m} \frac{\mathrm{d}^2}{\mathrm{d}x ^2} + V(x).
$$

パラメータは次の構造体で指定されます：

```
IPW = InfinitePotentialWell(L=1.0, m=1.0, ℏ=1.0)
```

$$
L
$$

は箱の長さ、$m$は粒子の質量、$\hbar$は縮小プランク定数（ディラック定数）です。

## 参考文献

  * [D. J. Griffiths, D. F. Schroeter, *Introduction to Quantum Mechanics* **第三版** (ケンブリッジ大学出版, 2018)](https://doi.org/10.1017/9781316995433) p.31, 2.2 無限平方井戸

## 証明

  * [固有関数と固有値](https://ja.wolframalpha.com/input?i2d=true&i=D%5B%5C%2840%29Sqrt%5BDivide%5B2%2Ca%5D%5Dsin%5C%2840%29Divide%5Bn%CF%80x%2Ca%5D%5C%2841%29%5C%2841%29%2C%7Bx%2C2%7D%5D)
  * [正規化](https://ja.wolframalpha.com/input?i=Integrate%5B%28%28Sqrt%5B2%2Fa%5Dsin%28%CF%80x%2Fa%29%29%29%5E2%2C+%7Bx%2C0%2Ca%7D%5D)
