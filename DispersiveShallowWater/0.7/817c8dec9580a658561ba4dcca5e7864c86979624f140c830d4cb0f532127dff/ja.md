```
HyperbolicSerreGreenNaghdiEquations1D(; bathymetry_type = bathymetry_mild_slope,
                                      gravity,
                                      eta0 = 0.0,
                                      lambda)
```

1次元の空間におけるSerre-Green-Naghdiシステムの双曲線近似。平坦な水深に対する方程式は次のように与えられます。

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x
    + \biggl( \frac{\lambda}{3} H (1 - H / h) \biggr)_x &= 0,\\
  h w_t + h v w_x &= \lambda (1 - H / h),\\
  H_t + H_x u &= w.
\end{aligned}
$$

双曲化されたSerre-Green-Naghdi方程式の未知数は、総水位 $\eta = h + b$ と速度 $v$ です。重力加速度 `gravity` は $g$ で表され、底の地形（バシメトリ） $b = \eta_0 - D$ です。したがって、水深は $h = \eta - \eta_0 + D$ で与えられます。総水位はしたがって $\eta = h + b$ で与えられます。

[`SerreGreenNaghdiEquations1D`](@ref) と比較して、2つの追加変数 $w \approx -h v_x$ と $H \approx h$ があります。Gavrilyuk らの元の論文では、変数 $H$ は $\eta$ と呼ばれています。ここでは、総水位に $\eta$ を使用し、双曲線近似で導入された補助変数に $H$ を使用します。

!!! note "初期条件"
    `HyperbolicSerreGreenNaghdiEquations1D` は、初期条件を指定するための2つのオプションを許可します：

    1. 変数の完全なセット `q = (η, v, D, w, H)` を返す
    2. 双曲線近似の制限システム [`SerreGreenNaghdiEquations1D`](@ref) に必要な変数の削減されたセット `q = (η, v, D)` を返す。残りの変数 `w` と `H` は、`solver` の導関数演算子を使用してデフォルトの初期化 $w \approx -h v_x$ と $H \approx h$ を使用して初期化されます。


この双曲線近似を得るために導入された緩和パラメータ `lambda` ($\lambda$) は、システムの剛性に影響を与えます。$\lambda \to \infty$ の場合、双曲線Serre-Green-Naghdi方程式は元の [`SerreGreenNaghdiEquations1D`](@ref) に収束します（少なくとも形式的に）。しかし、双曲線システムの波速は $\lambda$ の増加に伴って増加するため、明示的な時間積分法はより高価になります。

サポートされている `bathymetry_type` の2つのタイプ：

  * [`bathymetry_flat`](@ref): 平坦な水深（通常 $b = 0$ どこでも）
  * [`bathymetry_mild_slope`](@ref): 穏やかな傾斜近似を持つ変動する水深

穏やかな傾斜近似の場合、Serre-Green-Naghdi方程式は次のようになります。

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x
    + \biggl( \frac{\lambda}{3} H (1 - H / h) \biggr)_x
    + \biggl( g h + \frac{\lambda}{2} (1 - H / h) \biggr) b_x &= 0,\\
  h w_t + h v w_x &= \lambda (1 - H / h),\\
  H_t + H_x u + \frac{3}{2} b_x v &= w.
\end{aligned}
$$

双曲化されたSerre-Green-Naghdiシステムに関する参考文献は次のとおりです。

  * Favrie and Gavrilyuk. A rapid numerical method for solving Serre-Green-Naghdi equations describing long free surface gravity waves [DOI: 10.1088/1361-6544/aa712d](https://doi.org/10.1088/1361-6544/aa712d)
  * Busto, Dumbser, Escalante, Favrie, and Gavrilyuk. On High Order ADER Discontinuous Galerkin Schemes for First Order Hyperbolic Reformulations of Nonlinear Dispersive Systems [DOI: 10.1007/s10915-021-01429-8](https://doi.org/10.1007/s10915-021-01429-8)

ここで実装された半離散化は、次のものを保存します。

  * 総水質量（$h$ の積分）を線形不変量として
  * 総修正エネルギー

周期境界条件に対して（Ranocha と Ricchiuto (2024) を参照）。さらに、静止湖の定常解に対して良好にバランスが取れています。次を参照してください。

  * Hendrik Ranocha and Mario Ricchiuto (2024) Structure-preserving approximations of the Serre-Green-Naghdi equations in standard and hyperbolic form [arXiv: 2408.02665](https://arxiv.org/abs/2408.02665)
