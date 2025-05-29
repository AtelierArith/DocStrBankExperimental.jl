```
SvaerdKalischEquations1D(; bathymetry_type = bathymetry_variable, gravity,
                         eta0 = 0.0, alpha = 0.0, beta = 1/3, gamma = 0.0)
```

SvärdとKalischによる分散系（2023年）の1次元空間における方程式。可変水深に関する方程式は、保存変数によって次のように与えられます。

$$
\begin{aligned}
  h_t + (hv)_x &= (\hat\alpha(\hat\alpha(h + b)_x)_x)_x,\\
  (hv)_t + (hv^2)_x + gh(h + b)_x &= (\hat\alpha v(\hat\alpha(h + b)_x)_x)_x + (\hat\beta v_x)_{xt} + \frac{1}{2}(\hat\gamma v_x)_{xx} + \frac{1}{2}(\hat\gamma v_{xx})_x,
\end{aligned}
$$

ここで、$\hat\alpha^2 = \alpha\sqrt{gD}D^2$, $\hat\beta = \beta D^3$, $\hat\gamma = \gamma\sqrt{gD}D^3$です。係数$\alpha$, $\beta$, $\gamma$は無次元形式で提供され、$D = \eta_0 - b$は静水深であり、`eta0`は静水面（静止湖）です。方程式は原始変数で次のように書き換えることができます。

$$
\begin{aligned}
  \eta_t + ((\eta + D)v)_x &= (\hat\alpha(\hat\alpha\eta_x)_x)_x,\\
  v_t(\eta + D) - v((\eta + D)v)_x + ((\eta + D)v^2)_x + g(\eta + D)\eta_x &= (\hat\alpha v(\hat\alpha\eta_x)_x)_x - v(\hat\alpha(\hat\alpha\eta_x)_x)_x + (\hat\beta v_x)_{xt} + \frac{1}{2}(\hat\gamma v_x)_{xx} + \frac{1}{2}(\hat\gamma v_{xx})_x.
\end{aligned}
$$

Svärd-Kalisch方程式の未知量は、総水高$\eta$と速度$v$です。重力加速度`gravity`は$g$で示され、底の地形（バシメトリ）$b = \eta_0 - D$です。バシメトリの上の水高はしたがって$h = \eta - \eta_0 + D$で与えられます。

現在、方程式は一般的な可変水深のみをサポートしています。詳細は[`bathymetry_variable`](@ref)を参照してください。

`SvärdKalischEquations1D`は`SvaerdKalischEquations1D`のエイリアスです。

SvärdとKalischによる方程式は、SvärdとKalisch（2025年）で提示され、分析されています。ここで実装された半離散化は次のものを保存します。

  * 総水質量（$h$の積分）を線形不変量として
  * 総運動量（$h v$の積分）を平坦な水深に対する非線形不変量として
  * 総修正エネルギー

周期境界条件の下で（Lampert, Ranochaを参照）。さらに、静止湖の定常解に対して良好にバランスが取れています（LampertとRanocha（2024年）を参照）。

  * Magnus Svärd, Henrik Kalisch (2025) A novel energy-bounded Boussinesq model and a well-balanced and stable numerical discretization [arXiv: 2302.09924](https://arxiv.org/abs/2302.09924), [DOI: 10.1016/j.jcp.2024.113516](https://doi.org/10.1016/j.jcp.2024.113516)
  * Joshua Lampert, Hendrik Ranocha (2024) Structure-Preserving Numerical Methods for Two Nonlinear Systems of Dispersive Wave Equations [DOI: 10.48550/arXiv.2402.16669](https://doi.org/10.48550/arXiv.2402.16669)
