```
IdealGlmMhdMultiIonEquations2D(; gammas, charge_to_mass, 
                               gas_constants = zero(SVector{length(gammas),
                                                            eltype(gammas)}),
                               molar_masses = zero(SVector{length(gammas),
                                                           eltype(gammas)}),
                               ion_ion_collision_constants = zeros(eltype(gammas),
                                                           length(gammas),
                                                           length(gammas)),
                               ion_electron_collision_constants = zero(SVector{length(gammas),
                                                                               eltype(gammas)}),
                               electron_pressure = electron_pressure_zero,
                               electron_temperature = electron_pressure_zero,
                               initial_c_h = NaN)
```

2次元空間における理想的な圧縮可能な多イオンMHD方程式で、一般化されたラグランジュ乗数（GLM）発散クリーニング技術を強化しています。これは、各イオン種の運動量とエネルギー方程式が独立した熱的に完璧なプラズマの理想GLM-MHD方程式の多成分バリアントです。この実装は、方程式が無次元化されており、真空透磁率が$\mu_0 = 1$であると仮定しています。

複数のイオン種がある場合、比熱比`gammas`と質量対電荷比`charge_to_mass`はタプルとして渡す必要があります。例えば、`gammas=(1.4, 1.667)`のように。

イオン-イオンおよびイオン-電子衝突源項は、それぞれ[`source_terms_collision_ion_ion`](@ref)および[`source_terms_collision_ion_electron`](@ref)を使用して計算できます。

イオン-イオン衝突項については、オプションのキーワード引数`gas_constants`、`molar_masses`、および`ion_ion_collision_constants`を提供する必要があります。イオン-電子衝突項については、オプションのキーワード引数`gas_constants`、`molar_masses`、`ion_electron_collision_constants`、および`electron_temperature`が必要です。

  * **`gas_constants`**および**`molar_masses`**は、それぞれのイオン種の気体定数とモル質量を含むタプルです。**モル質量**は、比率を計算するためにのみ使用され、他の引数とは独立しているため、任意の単位系で提供できます。
  * **`ion_ion_collision_constants`**は、イオン種のペア間の衝突頻度を計算するための係数を含む対称行列です。例えば、`ion_ion_collision_constants[2, 3]`は、イオン種2とイオン種3の間の衝突係数を含みます。これらの定数は、気体の運動論的理論を使用して導出されます（例：*Schunk & Nagy, 2000*を参照）。これらは、*Schunk & Nagy (2000)*の表4.3にリストされている衝突係数$B_{st}$に関連していますが、イオン種$t$の分子量でスケーリングされており（すなわち、`ion_ion_collision_constants[2, 3] =` $B_{st}/m_{t}$）、一貫した物理単位で提供する必要があります（Schunk & Nagyは$cm^3 K^{3/2} / s$を使用）。これらの定数が衝突頻度を計算するためにどのように使用されるかについての詳細は、[`source_terms_collision_ion_ion`](@ref)を参照してください。
  * **`ion_electron_collision_constants`**は、各イオン種のイオン-電子衝突頻度を計算するための係数を含むタプルです。これらは、基本電荷で割った衝突係数`B_{se}`に対応します。イオン-電子衝突頻度も、気体の運動論的理論を使用して計算できます（例：*Schunk & Nagy, 2000*を参照）。これらの定数が衝突頻度を計算するためにどのように使用されるかについての詳細は、[`source_terms_collision_ion_electron`](@ref)を参照してください。
  * **`electron_temperature`**は、状態`u`の関数として電子温度を計算するために使用できる署名`electron_temperature(u, equations)`を持つ関数です。電子温度は、イオン-電子衝突源項の計算に関連しています。

引数`electron_pressure`は、状態`u`の関数として電子圧を計算する関数を渡すために使用できます。署名は`electron_pressure(u, equations)`です。電子圧の勾配は、ローレンツフラックスおよび非保守項の計算に関連しています。デフォルトでは、電子圧はゼロです。

引数`initial_c_h`は、GLM発散クリーニング速度を設定するために使用できます。`initial_c_h = 0`は発散クリーニングを無効にします。コールバック[`GlmSpeedCallback`](@ref)を使用して、タイムステップサイズに応じてGLM発散クリーニング速度を調整できます。

参考文献：

  * G. Toth, A. Glocer, Y. Ma, D. Najib, Multi-Ion Magnetohydrodynamics 429 (2010). Numerical  Modeling of Space Plasma Flows, 213–218. [Bib Code: Code: 2010ASPC..429..213T](https://adsabs.harvard.edu/full/2010ASPC..429..213T).
  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).
  * Schunk, R. W., & Nagy, A. F. (2000). Ionospheres: Physics, plasma physics, and chemistry.  Cambridge university press. [DOI: 10.1017/CBO9780511635342](https://doi.org/10.1017/CBO9780511635342).

!!! info "多イオンGLM-MHD方程式は源項を必要とします"
    複数のイオン種がある場合、多イオンGLM-MHD方程式は常に[`source_terms_lorentz`](@ref)と共に使用する必要があります。

