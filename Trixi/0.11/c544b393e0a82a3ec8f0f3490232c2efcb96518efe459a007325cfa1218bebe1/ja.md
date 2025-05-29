```
flux_wintermeyer_etal(u_ll, u_rr, orientation_or_normal_direction,
                      equations::ShallowWaterEquations2D)
```

全エネルギー保存（浅水方程式の数学的エントロピー）分割形式。底面の地形がゼロでない場合、このスキームは `volume_flux` として使用されるときに良好にバランスが取れます。 `surface_flux` には、[`flux_wintermeyer_etal`](@ref) または [`flux_fjordholm_etal`](@ref) のいずれかを使用して、バランスの取れた状態とエントロピーの保存を確保できます。

さらなる詳細は、論文の定理1に記載されています：

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner, David A. Kopriva (2017) 不連続バスシメトリを持つ非構造的曲線メッシュ上の二次元浅水方程式のためのエントロピー安定ノード不連続ガレルキン法 [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
