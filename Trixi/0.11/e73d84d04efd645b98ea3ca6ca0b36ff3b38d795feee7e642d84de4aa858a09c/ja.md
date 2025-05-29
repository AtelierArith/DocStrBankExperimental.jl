```
flux_nonconservative_audusse_etal(u_ll, u_rr, orientation::Integer,
                                  equations::ShallowWaterEquations1D)
```

非対称の二点表面フラックスで、非保守的（ソース）項を離散化します。この離散化は、保守変数に対して `hydrostatic_reconstruction_audusse_etal` を使用します。

この静水圧再構成により、有限体積数値フラックスが不連続な底面地形に対して良好にバランスが取れることが保証されます [`ShallowWaterEquations1D`](@ref)。整合性を確保するために、[`FluxHydrostaticReconstruction`](@ref) および [`hydrostatic_reconstruction_audusse_etal`](@ref) と一緒に使用する必要があります。

静水圧再構成とその動機に関する詳細は、以下の文献に記載されています。

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) A fast and stable well-balanced scheme with hydrostatic reconstruction for shallow water flows [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)
