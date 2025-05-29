```
IdealGlmMhdMultiIonEquations3D(; gammas, charge_to_mass, 
                               electron_pressure = electron_pressure_zero,
                               initial_c_h = NaN)
```

三次元空間における理想的な圧縮性多イオンMHD方程式で、一般化されたラグランジュ乗数（GLM）によるダイバージェンスクリーニング技術が強化されています。これは、各イオン種に対して独立した運動量とエネルギー方程式を持つ、熱的に完璧なプラズマのための理想的なGLM-MHD方程式の多成分バリアントです。この実装は、方程式が無次元化されていることを前提としており、真空透磁率は $\mu_0 = 1$ です。

複数のイオン種がある場合、比熱比 `gammas` と質量に対する電荷比 `charge_to_mass` はタプルとして渡す必要があります。例えば、`gammas=(1.4, 1.667)` のようにします。

引数 `electron_pressure` は、状態 `u` の関数として電子圧を計算する関数を渡すために使用できます。シグネチャは `electron_pressure(u, equations)` です。デフォルトでは、電子圧はゼロです。

引数 `initial_c_h` は、GLMダイバージェンスクリーニング速度を設定するために使用できます。`initial_c_h = 0` はダイバージェンスクリーニングを無効にします。コールバック [`GlmSpeedCallback`](@ref) を使用して、タイムステップサイズに応じてGLMダイバージェンスクリーニング速度を調整できます。

参考文献：

  * G. Toth, A. Glocer, Y. Ma, D. Najib, Multi-Ion Magnetohydrodynamics 429 (2010). Numerical  Modeling of Space Plasma Flows, 213–218.
  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).

!!! info "多イオンGLM-MHD方程式はソース項を必要とします"
    複数のイオン種がある場合、多イオンGLM-MHD方程式は常に [`source_terms_lorentz`](@ref) と共に使用する必要があります。

