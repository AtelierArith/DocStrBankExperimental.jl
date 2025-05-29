```
min_max_speed_einfeldt(u_ll, u_rr, orientation, equations::CompressibleEulerEquations1D)
```

圧縮性オイラー方程式のためのHLLE（Harten-Lax-van Leer-Einfeldt）フラックスを計算します。内部エネルギーと密度が数値フラックスの計算中に正であることを保証するために、Einfeldtによって開発された信号速度の特別な推定とリーマン問題の線形化を使用しています。

元の出版物：

  * Bernd Einfeldt (1988) On Godunov-type methods for gas dynamics. [DOI: 10.1137/0725021](https://doi.org/10.1137/0725021)

簡潔に要約：

  * Siddhartha Mishra, Ulrik Skre Fjordholm and Rémi Abgrall 数値法による保存則と関連方程式。 [Link](https://metaphor.ethz.ch/x/2019/hs/401-4671-00L/literature/mishra_hyperbolic_pdes.pdf)
