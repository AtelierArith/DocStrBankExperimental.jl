```
BBMEquation1D(; gravity, D = 1.0, eta0 = 0.0, split_form = true)
```

BBM（ベンジャミン–ボナ–マホニー）方程式は1次元の空間における方程式です。この方程式は次のように表されます。

$$
\begin{aligned}
  \eta_t + \sqrt{gD}\eta_x + \frac{3}{2}\sqrt{\frac{g}{D}}\eta\eta_x - \frac{1}{6}D^2\eta_{xxt} &= 0.
\end{aligned}
$$

BBM方程式の未知数は総水位$\eta$です。重力加速度`gravity`は$g$で表され、定数の底面地形（バシメトリ）$b = \eta_0 - D$、ここで$\eta_0$は定常水面、$D$は定常水深です。したがって、バシメトリの上の水位は$h = \eta - \eta_0 + D$で与えられます。BBM方程式は$\eta_0 = 0$の場合のみ実装されています。

方程式は平坦なバシメトリのみをサポートします。

BBM方程式は最初にBenjamin、Bona、Mahony（1972）で記述されました。ここで実装されている半離散化は、`split_form = true`の場合はRanocha、Mitsotakis、Ketcheson（2020）で、`split_form = false`の場合はLinders、Ranocha、Birken（2023）で開発されました。`split_form`が`true`の場合、半離散化では分割形式が使用され、次のものが保存されます。

  * 総水質量（$h$の積分）を線形不変量として
  * 二次不変量（$1/2\eta(\eta - 1/6D^2\eta_{xx})$の積分、または周期境界条件の場合は同等に$1/2(\eta^2 + 1/6D^2\eta_x^2)$）、ここでは[`energy_total_modified`](@ref)（および[`entropy_modified`](@ref)）と呼ばれ、解の導関数を含むため

周期境界条件の場合。`split_form`が`false`の場合、半離散化は次のものを保存します。

  * 総水質量（$h$の積分）を線形不変量として
  * ハミルトニアン（$1/4\sqrt{g/D}\eta^3 + 1/2\sqrt{gD}\eta^2$の積分）（[`hamiltonian`](@ref）を参照）

周期境界条件の場合。

  * Thomas B. Benjamin、Jerry L. Bona、John J. Mahony（1972）非線形分散系における長波のモデル方程式 [DOI: 10.1098/rsta.1972.0032](https://doi.org/10.1098/rsta.1972.0032)
  * Hendrik Ranocha、Dimitrios Mitsotakis、David I. Ketcheson（2020）分散波方程式のための保守的数値法の広範なクラス [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
  * Viktor Linders、Hendrik Ranocha、Philipp Birken（2023）反復法からのエントロピー成長の解決 [DOI: 10.1007/s10543-023-00992-w](https://doi.org/10.1007/s10543-023-00992-w)
