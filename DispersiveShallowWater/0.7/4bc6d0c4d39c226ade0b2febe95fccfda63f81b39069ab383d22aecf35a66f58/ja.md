```
SerreGreenNaghdiEquations1D(; bathymetry_type = bathymetry_variable,
                            gravity, eta0 = 0.0)
```

1次元空間におけるSerre-Green-Naghdiシステム。平坦な水深に対する方程式は次のように与えられます。

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t - \frac{1}{3} (h^3 v_{tx})_x + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x + p_x &= 0,\\
  p &= \frac{1}{3} h^3 v_{x}^2 - \frac{1}{3} h^3 v v_{xx}.
\end{aligned}
$$

Serre-Green-Naghdi方程式の未知量は、総水位$\eta = h + b$と速度$v$です。重力加速度`gravity`は$g$で表され、底の地形（バシメトリ）$b = \eta_0 - D$です。したがって、水深は$h = \eta - \eta_0 + D$で与えられます。総水位はしたがって$\eta = h + b$で与えられます。

サポートされている`bathymetry_type`の3つのタイプは次のとおりです：

  * [`bathymetry_flat`](@ref): 平坦な水深（通常$b = 0$）
  * [`bathymetry_mild_slope`](@ref): 穏やかな傾斜近似を持つ変動する水深
  * [`bathymetry_variable`](@ref): 一般的な変動する水深

穏やかな傾斜近似の場合、Serre-Green-Naghdi方程式は次のようになります。

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t - \frac{1}{3} (h^3 v_{tx})_x + \frac{1}{2} (h^2 b_x v_t)_x - \frac{1}{2} h^2 b_x v_{tx} + \frac{3}{4} h b_x^2 v_t
    + \frac{1}{2} g (h^2)_x + g h b_x + \frac{1}{2} h (v^2)_x
    + p_x + \frac{3}{2} \frac{p}{h} b_x &= 0,\\
  p &= \frac{1}{3} h^3 v_{x}^2 - \frac{1}{3} h^3 v v_{xx}
    + \frac{1}{2} h^2 v (b_x v)_x.
\end{aligned}
$$

穏やかな傾斜近似なしの変動する水深の一般的な場合、Serre-Green-Naghdi方程式は次のようになります。

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t - \frac{1}{3} (h^3 v_{tx})_x + \frac{1}{2} (h^2 b_x v_t)_x - \frac{1}{2} h^2 b_x v_{tx} + h b_x^2 v_t
    + \frac{1}{2} g (h^2)_x + g h b_x + \frac{1}{2} h (v^2)_x
    + p_x + \frac{3}{2} \frac{p}{h} b_x + \psi b_x &= 0,\\
  p &= \frac{1}{3} h^3 v_{x}^2 - \frac{1}{3} h^3 v v_{xx}
    + \frac{1}{2} h^2 v (b_x v)_x,\\
  \psi &= \frac{1}{4} h v (b_x v)_x.
\end{aligned}
$$

Serre-Green-Naghdiシステムに関する参考文献は次のとおりです。

  * Serre (1953) Contribution â l'étude des écoulements permanents et variables dans les canaux [DOI: 10.1051/lhb/1953034](https://doi.org/10.1051/lhb/1953034)
  * Green and Naghdi (1976) A derivation of equations for wave propagation in water of variable depth [DOI: 10.1017/S0022112076002425](https://doi.org/10.1017/S0022112076002425)

ここで実装された半離散化は次のものを保存します。

  * 総水質量（$h$の積分）を線形不変量として
  * 総運動量（$h v$の積分）を水深が一定の場合の非線形不変量として
  * 総修正エネルギー

周期境界条件の場合（RanochaとRicchiuto (2024)を参照）。さらに、静止湖の定常解に対して良好にバランスが取れています。参照：

  * Hendrik RanochaとMario Ricchiuto (2024) Structure-preserving approximations of the Serre-Green-Naghdi equations in standard and hyperbolic form [arXiv: 2408.02665](https://arxiv.org/abs/2408.02665)
