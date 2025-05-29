```
BloodFlowEquations2D(;h,rho=1.0,xi=0.25)
```

ナビエ-ストークス方程式から導出された二次元血流方程式を、薄動脈の仮定の下で定義します。このモデルは、二つの空間次元（s, θ）における柔軟な動脈に沿った血流の動態を記述します。

### パラメータ

  * `h::T`: 動脈の壁の厚さ。
  * `rho::T`: 流体の密度（デフォルトは1.0）。
  * `xi::T`: ポアソン比（デフォルトは0.25）。
  * `nu::T`: 粘度係数。

支配方程式は、質量と運動量の保存を考慮し、動脈の柔軟性、曲率、および摩擦損失の影響を組み込んでいます。

$$
\left\{\begin{aligned}
    \frac{\partial a}{\partial t} + \frac{\partial}{\partial \theta}\left( \frac{Q_{R\theta}}{A} \right) + \frac{\partial}{\partial s}(Q_s) &= 0 \\
    \frac{\partial Q_{R\theta}}{\partial t} + \frac{\partial}{\partial \theta}\left(\frac{Q_{R\theta}^2}{2A^2} + A P(a)\right) + \frac{\partial}{\partial s}\left( \frac{Q_{R\theta}Q_s}{A} \right) &= P(a) \frac{\partial A}{\partial \theta} - 2 R k \frac{Q_{R\theta}}{A} + \frac{2R}{3} \mathcal{C}\sin \theta \frac{Q_s^2}{A} \\
    \frac{\partial Q_{s}}{\partial t} + \frac{\partial}{\partial \theta}\left(\frac{Q_{R\theta} Q_s}{A^2} \right) + \frac{\partial}{\partial s}\left( \frac{Q_s^2}{A} - \frac{Q_{R\theta}^2}{2A^2} + A P(a) \right) &= P(a) \frac{\partial A}{\partial s} - R k \frac{Q_s}{A} - \frac{2R}{3} \mathcal{C}\sin \theta \frac{Q_s Q_{R\theta}}{A^2} \\
    P(a) &= P_{ext} + \frac{Eh}{\sqrt{2}\left(1-\xi^2\right)}\frac{\sqrt{A} - \sqrt{A_0}}{A_0} \\
    R &= \sqrt{2A}
\end{aligned}\right.
$$
