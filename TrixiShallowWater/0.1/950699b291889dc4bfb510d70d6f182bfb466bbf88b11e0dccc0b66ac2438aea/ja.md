```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterTwoLayerEquations1D)
```

非対称パス保存型二点体積フラックスで、底面地形の勾配を含む非保守的（ソース）項を離散化し、両層の運動量を結びつける追加項を含みます。

これは、[`flux_nonconservative_wintermeyer_etal`](@ref) の修正版で、[`flux_wintermeyer_etal`](@ref) と組み合わせることで、体積と表面の両方でエントロピー保存とバランスの良さを提供します。

詳細については、以下を参照してください：

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
