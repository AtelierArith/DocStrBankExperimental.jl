```
flux_nonconservative_central(u_ll, u_rr, orientation::Integer,
                             equations::IdealGlmMhdMultiIonEquations3D)
```

中央非保守二点「フラックス」で、対称部分は標準的な平均を用いて計算されます。この用語は、[`flux_central`](@ref) と [`VolumeIntegralFluxDifferencing`](@ref) と共に使用することで、マルチイオンGLM-MHDシステムの「標準的な」（弱形式の）DGSEM離散化を生成します。このフラックスは、`surface_flux = (flux_lax_friedrichs, flux_nonconservative_central)`を使用して、標準的なローカルLax-Friedrichsフラックスを構築するためにも使用できます。

!!! info "Trixi.jlにおける非保守フラックスの使用とスケーリング"
    この関数で実装されている中央非保守フラックスは、対称部分が標準的な平均であるローカル部分と対称部分の積として書かれています。これらのフラックスは、保守フラックスと同じ方法で使用されることを意図しています（すなわち、体積および表面積分の両方でflux + flux_noncons）。このルーチンでは、非保守フラックスはTrixi.jlコードで使用されるたびに0.5で乗算されるため、フラックスは2倍されます。


この用語は、4つの個別の非保守項で構成されています：

1. 磁場の発散がゼロでないプラズマに対して生じるGodunov-Powell項で、電荷平均速度の関数として評価されます。
2. 電子圧勾配がゼロのときに一つのイオン種の限界で保守項となるローレンツ力項。
3. 一つのイオン種の限界で消失する「マルチイオン」項。
4. ガリレイ不変性のために必要なGLM項。
