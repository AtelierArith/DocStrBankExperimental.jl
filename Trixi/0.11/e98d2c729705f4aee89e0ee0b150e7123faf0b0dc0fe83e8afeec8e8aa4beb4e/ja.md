```
flux_nonconservative_central(u_ll, u_rr, orientation::Integer,
                             equations::IdealGlmMhdMultiIonEquations2D)
```

中央非保守二点「フラックス」で、対称部分は標準的な平均を用いて計算されます。この項を[`flux_central`](@ref)および[`VolumeIntegralFluxDifferencing`](@ref)と共に使用することで、マルチイオンGLM-MHDシステムの「標準的な」（弱形式の）DGSEM離散化が得られます。このフラックスは、`surface_flux = (flux_lax_friedrichs, flux_nonconservative_central)`を使用して標準的なローカルLax-Friedrichsフラックスを構築するためにも使用できます。

!!! info "Trixiにおける非保守フラックスの使用とスケーリング"
    この関数で実装されている中央非保守フラックスは、対称部分が標準的な平均であるローカル部分と対称部分の積として書かれています。これらのフラックスは、保守フラックス（すなわち、体積および表面積分の両方でflux + flux_nonconsとして）と同じ方法で使用されることを意図しています。このルーチンでは、非保守フラックスはTrixiコードで使用されるときに常に0.5で乗算されるため、フラックスは2倍されます。


この項は、4つの個別の非保守項で構成されています：

1. 磁場の発散がゼロでないプラズマに対して生じるGodunov-Powell項で、荷電平均速度の関数として評価されます。
2. 電子圧勾配がゼロのときに一つのイオン種の限界で保守項となるローレンツ力項。
3. 一つのイオン種の限界でゼロになる「マルチイオン」項。
4. ガリレイ不変性のために必要なGLM項。
