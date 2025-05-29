```
flux_nonconservative_wintermeyer_etal(u_ll, u_rr, orientation::Integer,
                                      equations::ShallowWaterEquations2D)
flux_nonconservative_wintermeyer_etal(u_ll, u_rr,
                                      normal_direction::AbstractVector,
                                      equations::ShallowWaterEquations2D)
```

非対称の二点体積フラックスは、底の地形の勾配を含む非保守的（ソース）項を離散化します [`ShallowWaterEquations2D`](@ref)。

`surface_flux` には、バランスの良さとエントロピー保存を確保するために、[`flux_wintermeyer_etal`](@ref) または [`flux_fjordholm_etal`](@ref) を使用できます。

さらなる詳細は、以下の論文にあります：

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner and David A. Kopriva (2017) An entropy stable nodal discontinuous Galerkin method for the two dimensional shallow water equations on unstructured curvilinear meshes with discontinuous bathymetry [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on curvilinear meshes [DOI: 10.48550/arXiv.2306.12699](https://doi.org/10.48550/arXiv.2306.12699)
