## モデル

このモデルは時間に依存しないシュレーディンガー方程式で記述されます。

$$
  \hat{H} \psi(x,y,z) = E \psi(x,y,z),
$$

およびハミルトニアン

$$
  \hat{H} = - \frac{\hbar^2}{2m} \left(\frac{\partial^2}{\partial x ^2} + \frac{\partial^2}{\partial y ^2} + \frac{\partial^2}{\partial z ^2}\right) + V(x,y,z).
$$

パラメータは以下の構造体で指定されます。

```
IPW3D = InfinitePotentialWell3D(L=[1.0,1.0,1.0], m=1.0, ℏ=1.0)
```

$$
L
$$

は $x$、$y$、$z$ 方向の箱の長さのベクトルであり、$m$ は粒子の質量、$\hbar$ は縮小プランク定数（ディラック定数）です。

## 参考文献

  * [D. A. McQuarrie, J. D. Simon, *Physical chemistry : a molecular approach* (University Science Books, 1997)](https://uscibooks.aip.org/books/physical-chemistry-a-molecular-approach/) p.90, 3-9. 三次元ボックス内の粒子の問題は一次元の場合の単純な拡張です。
