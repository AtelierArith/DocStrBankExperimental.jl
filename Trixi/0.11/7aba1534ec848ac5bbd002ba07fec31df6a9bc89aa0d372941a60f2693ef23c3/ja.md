```
flux_nonconservative_fjordholm_etal(u_ll, u_rr, orientation::Integer,
                                    equations::ShallowWaterEquations2D)
flux_nonconservative_fjordholm_etal(u_ll, u_rr,
                                    normal_direction::AbstractVector,
                                    equations::ShallowWaterEquations2D)
```

非対称の二点表面フラックスは、底面地形の勾配を含む非保守的（ソース）項を離散化します [`ShallowWaterEquations2D`](@ref)。

このフラックスは、エントロピー保存とバランスの良さを確保するために、インターフェースで [`flux_fjordholm_etal`](@ref) と一緒に使用できます。

元の有限体積定式化に関する詳細は以下にあります。

  * Ulrik S. Fjordholm, Siddhartha Mishra and Eitan Tadmor (2011) Well-balanced and energy stable schemes for the shallow water equations with discontinuous topography [DOI: 10.1016/j.jcp.2011.03.042](https://doi.org/10.1016/j.jcp.2011.03.042)

および曲線状の2Dケースについては、以下の論文にあります。

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner and David A. Kopriva (2017) An entropy stable nodal discontinuous Galerkin method for the two dimensional shallow water equations on unstructured curvilinear meshes with discontinuous bathymetry [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
