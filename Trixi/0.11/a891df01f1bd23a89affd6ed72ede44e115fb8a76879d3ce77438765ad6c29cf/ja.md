```
flux_wintermeyer_etal(u_ll, u_rr, orientation,
                      equations::ShallowWaterEquations1D)
```

全エネルギー保存（浅水方程式の数学的エントロピー）分割形式。底面の地形がゼロでない場合、このスキームは `volume_flux` として使用されるときに良好にバランスが取れます。 `surface_flux` には、[`flux_wintermeyer_etal`](@ref) または [`flux_fjordholm_etal`](@ref) のいずれかを使用して、バランスの良さとエントロピーの保存を確保できます。

さらなる詳細は、論文の定理1に記載されています：

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner and David A. Kopriva (2017) An entropy stable nodal discontinuous Galerkin method for the two dimensional shallow water equations on unstructured curvilinear meshes with discontinuous bathymetry [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
