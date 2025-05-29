```
BBMBBMEquations1D(; bathymetry_type = bathymetry_variable,
                  gravity, eta0 = 0.0)
```

BBM-BBM（ベンジャミン–ボナ–マホニー）システムは1次元の空間におけるものです。平坦なバシメトリに対する方程式は次のように与えられます。

$$
\begin{aligned}
  \eta_t + ((\eta + D)v)_x - \frac{1}{6}D^2\eta_{xxt} &= 0,\\
  v_t + g\eta_x + \left(\frac{1}{2}v^2\right)_x - \frac{1}{6}D^2v_{xxt} &= 0.
\end{aligned}
$$

BBM-BBM方程式の未知数は、総水位$\eta$と速度$v$です。重力加速度`gravity`は$g$で表され、定数の底面地形（バシメトリ）$b = \eta_0 - D$です。したがって、バシメトリ上の水位は$h = \eta - \eta_0 + D$で与えられます。BBM-BBM方程式は$\eta_0 = 0$の場合にのみ実装されています。

サポートされている`bathymetry_type`の2つのタイプは次のとおりです：

  * [`bathymetry_flat`](@ref): 平坦なバシメトリ（通常は$b = 0$の場所）
  * [`bathymetry_variable`](@ref): 一般的な変動バシメトリ

変動バシメトリの一般的な場合におけるBBM-BBM方程式は次のようになります。

$$
\begin{aligned}
  \eta_t + ((\eta + D)v)_x - \frac{1}{6}(D^2\eta_{xt})_x &= 0,\\
  v_t + g\eta_x + \left(\frac{1}{2}v^2\right)_x - \frac{1}{6}(D^2v_t)_{xx} &= 0.
\end{aligned}
$$

BBM-BBMシステムの参考文献はBona et al. (1998)にあります。ここで実装された半離散化は、Ranocha et al. (2020)で平坦なバシメトリのために開発され、LampertとRanocha (2024)で変動バシメトリのために一般化されました。これは次のものを保存します。

  * 総水質量（$h$の積分）を線形不変量として
  * 平坦なバシメトリに対する総速度（$v$の積分）を線形不変量として
  * 総エネルギー

周期境界条件に対して（Lampert, Ranochaを参照）。反射境界条件に対して、半離散化は次のものを保存します。

  * 総水（$h$の積分）を線形不変量として
  * 総エネルギー。

さらに、静止湖の定常解に対して良好にバランスが取れています。LampertとRanocha (2024)を参照してください。

  * Jerry L. Bona, Min Chen (1998) A Boussinesq system for two-way propagation of nonlinear dispersive waves [DOI: 10.1016/S0167-2789(97)00249-2](https://doi.org/10.1016/S0167-2789(97)00249-2)
  * Hendrik Ranocha, Dimitrios Mitsotakis, David I. Ketcheson (2020) A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
  * Joshua Lampert, Hendrik Ranocha (2024) Structure-Preserving Numerical Methods for Two Nonlinear Systems of Dispersive Wave Equations [DOI: 10.48550/arXiv.2402.16669](https://doi.org/10.48550/arXiv.2402.16669)
