```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterMultiLayerEquations2D)
flux_nonconservative_ersing_etal(u_ll, u_rr,
                                 normal_direction::AbstractVector,
                                 equations::ShallowWaterMultiLayerEquations2D)
```

非対称パス保存型二点フラックスは、層間の結合からの底面地形と水位の勾配を含む非保守的（ソース）項を離散化します [`ShallowWaterMultiLayerEquations2D`](@ref)。

底面地形がゼロでない場合、このスキームは [`flux_ersing_etal`](@ref) と一緒に使用するとバランスが取れます。

二層設定では、この組み合わせは以下のフラックスに相当します：

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
