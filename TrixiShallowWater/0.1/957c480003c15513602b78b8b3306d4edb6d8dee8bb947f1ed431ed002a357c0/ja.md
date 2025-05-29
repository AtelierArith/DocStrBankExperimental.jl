```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterTwoLayerEquations2D)
flux_nonconservative_ersing_etal(u_ll, u_rr,
                                 normal_direction::AbstractVector,
                                 equations::ShallowWaterTwoLayerEquations2D)
```

非対称パス保存型二点体積フラックスは、底面地形の勾配を含む非保守的（ソース）項を離散化し、両層の運動量を結合する追加項を含みます [`ShallowWaterTwoLayerEquations2D`](@ref)。

これは、エントロピー保存と体積および表面のバランスを保つために [`flux_wintermeyer_etal`](@ref) と組み合わせた際に、エントロピー保存を提供するように修正された [`flux_nonconservative_wintermeyer_etal`](@ref) のバージョンです。

詳細については、以下を参照してください：

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
