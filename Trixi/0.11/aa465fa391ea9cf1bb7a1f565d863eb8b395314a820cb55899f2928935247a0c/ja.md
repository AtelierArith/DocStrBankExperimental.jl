```
DragCoefficientShearStress2D(aoa, rho_inf, u_inf, l_inf)
```

抗力係数を計算します

$$
C_{D,f} \coloneqq \frac{\oint_{\partial \Omega} \boldsymbol \tau_w \cdot \psi_D \, \mathrm{d} S}
                        {0.5 \rho_{\infty} U_{\infty}^2 L_{\infty}}
$$

境界に沿った壁せん断応力ベクトル $\tau_w$ に基づいています。2Dでは、自由流に対する接線単位ベクトル $\psi_D$ は次のように与えられます。

$$
\psi_D \coloneqq \begin{pmatrix} \cos(\alpha) \\ \sin(\alpha) \end{pmatrix}
$$

ここで、$\alpha$ は迎角です。境界情報と半離散化を保存する [`AnalysisSurfaceIntegral`](@ref) と併用することを想定しています。

  * `aoa::Real`: ラジアン単位の迎角（エアフォイルなど）
  * `rho_inf::Real`: 自由流密度
  * `u_inf::Real`: 自由流速度
  * `l_inf::Real`: 幾何の基準長さ（例：エアフォイルの弦長）
