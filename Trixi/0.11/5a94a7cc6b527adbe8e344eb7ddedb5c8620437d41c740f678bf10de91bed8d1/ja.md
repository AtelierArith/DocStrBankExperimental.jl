```
flux_nonconservative_ruedaramirez_etal(u_ll, u_rr,
                                       orientation_or_normal_direction,
                                       equations::IdealGlmMhdMultiIonEquations3D)
```

エントロピー保存非保守二点「フラックス」は以下に記載されています。

  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).

!!! info "Trixi.jlにおける非保守フラックスの使用とスケーリング"
    上記の参考文献で導出された非保守フラックスは、局所的および対称的な部分の積として記述されており、保守フラックスと同様に使用されることを意図しています（すなわち、体積および表面積分の両方でフラックス + flux_noncons）。このルーチンでは、非保守フラックスはTrixi.jlコードで使用されるたびに0.5で乗算されるため、フラックスは2倍されます。


この項は、4つの個別の非保守項で構成されています：

1. 磁場の発散がゼロでないプラズマに対して生じるGodunov-Powell項で、荷電平均速度の関数として評価されます。
2. 電子圧勾配がゼロのときに一つのイオン種の限界で保守項となるローレンツ力項。
3. 一つのイオン種の限界で消失する「多イオン」項。
4. ガリレイ不変性のために必要なGLM項。
