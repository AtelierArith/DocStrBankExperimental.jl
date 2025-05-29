```
LiftCoefficientPressure2D(aoa, rho_inf, u_inf, l_inf)
```

揚力係数を計算します

$$
C_{L,p} \coloneqq \frac{\oint_{\partial \Omega} p \boldsymbol n \cdot \psi_L \, \mathrm{d} S}
                        {0.5 \rho_{\infty} U_{\infty}^2 L_{\infty}}
$$

境界に沿った圧力分布に基づいています。2Dでは、自由流に対する法線単位ベクトル $\psi_L$ は次のように与えられます

$$
\psi_L \coloneqq \begin{pmatrix} -\sin(\alpha) \\ \cos(\alpha) \end{pmatrix}
$$

ここで、$\alpha$ は迎角です。境界情報と半離散化を保存する [`AnalysisSurfaceIntegral`](@ref) と併用することを想定しています。

  * `aoa::Real`: ラジアン単位の迎角（空力翼など）
  * `rho_inf::Real`: 自由流密度
  * `u_inf::Real`: 自由流速度
  * `l_inf::Real`: 幾何の基準長さ（例：空力翼の弦長）
