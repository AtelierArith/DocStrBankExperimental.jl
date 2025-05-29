```
flux_nonconservative_audusse_etal(u_ll, u_rr, orientation::Integer,
                                  equations::ShallowWaterEquations2D)
flux_nonconservative_audusse_etal(u_ll, u_rr,
                                  normal_direction::AbstractVector,
                                  equations::ShallowWaterEquations2D)
```

非対称の二点表面フラックスで、非保守的（ソース）項を離散化します。この離散化は、保守変数に対して `hydrostatic_reconstruction_audusse_etal` を使用します。

この静水圧再構成は、有限体積数値フラックスが不連続な底面地形に対してバランスが取れていることを保証します [`ShallowWaterEquations2D`](@ref)。整合性を確保するために、[`FluxHydrostaticReconstruction`](@ref) および [`hydrostatic_reconstruction_audusse_etal`](@ref) と一緒に使用する必要があります。

静水圧再構成の詳細とその動機については、以下を参照してください。

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) A fast and stable well-balanced scheme with hydrostatic reconstruction for shallow water flows [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)
