```
reinit!(s::HamiltonJacobiEvolution{O},φ,γ) where O
```

ハミルトン・ジャコビ進化を使用して再初期化方程式を解きます。

# 再初期化方程式

$$
\frac{\partial\phi}{\partial t} + \mathrm{sign}(\phi_0)(\lVert\boldsymbol{\nabla}\phi\rVert-1) = 0,
$$

ここで、$\phi(0,\boldsymbol{x})=\phi_0(\boldsymbol{x})$ および $\boldsymbol{x}\in D,~t\in(0,T)$ です。

# 引数

  * `s::HamiltonJacobiEvolution{O}`: メソッド
  * `φ`: 自由度のベクトルとしてのレベルセット関数
  * `γ`: 時間ステップサイズに対する係数。
