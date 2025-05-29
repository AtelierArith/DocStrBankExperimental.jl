```
min_max_speed_einfeldt(u_ll, u_rr, normal_direction, equations::CompressibleEulerEquations3D)
```

圧縮可能なオイラー方程式のためのHLLE（Harten-Lax-van Leer-Einfeldt）フラックスを計算します。内部エネルギーと密度が数値フラックスの計算中に正であることを保証するために、Einfeldtによって開発された信号速度の特別な推定とリーマン問題の線形化を行います。

  * Bernd Einfeldt (1988) On Godunov-type methods for gas dynamics. [DOI: 10.1137/0725021](https://doi.org/10.1137/0725021)
  * Bernd Einfeldt, Claus-Dieter Munz, Philip L. Roe and Björn Sjögreen (1991) On Godunov-type methods near low densities. [DOI: 10.1016/0021-9991(91)90211-3](https://doi.org/10.1016/0021-9991(91)90211-3)
