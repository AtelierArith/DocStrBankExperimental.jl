```
min_max_speed_einfeldt(u_ll, u_rr, orientation, equations::CompressibleEulerEquations3D)
```

圧縮性オイラー方程式のためのHLLE（Harten-Lax-van Leer-Einfeldt）フラックスを計算します。内部エネルギーと密度が数値フラックスの計算中に正のままであることを保証するために、Einfeldtによって開発された信号速度の特別な推定とリーマン問題の線形化を使用しています。

  * Bernd Einfeldt (1988) On Godunov-type methods for gas dynamics. [DOI: 10.1137/0725021](https://doi.org/10.1137/0725021)
  * Bernd Einfeldt, Claus-Dieter Munz, Philip L. Roe and Björn Sjögreen (1991) On Godunov-type methods near low densities. [DOI: 10.1016/0021-9991(91)90211-3](https://doi.org/10.1016/0021-9991(91)90211-3)
