```
evolve!(s::HamiltonJacobiEvolution{O},φ,vel,γ) where O
```

ハミルトン・ヤコビ進化方程式を `HamiltonJacobiEvolution` を使用して解きます。

# ハミルトン・ヤコビ進化方程式

$$
\frac{\partial\phi}{\partial t} + V(\boldsymbol{x})\lVert\boldsymbol{\nabla}\phi\rVert = 0,
$$

ここで、$\phi(0,\boldsymbol{x})=\phi_0(\boldsymbol{x})$ かつ $\boldsymbol{x}\in D,~t\in(0,T)$ です。

# 引数

  * `s::HamiltonJacobiEvolution{O}`: メソッド
  * `φ`: 自由度のベクトルとしてのレベルセット関数
  * `vel`: 自由度のベクトルとしての法線速度
  * `γ`: 時間ステップサイズに対する係数。
