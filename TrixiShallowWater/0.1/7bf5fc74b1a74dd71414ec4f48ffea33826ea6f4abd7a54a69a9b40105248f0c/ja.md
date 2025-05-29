```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterTwoLayerEquations1D)
```

非対称パス保存型二点フラックスで、層間の結合からの底面地形と水位の勾配を含む非保守的（ソース）項を離散化します。また、非保守的圧力定式化 [`ShallowWaterMultiLayerEquations1D`](@ref) を含みます。

底面地形がゼロでない場合、このスキームは [`flux_ersing_etal`](@ref) と併用すると良好にバランスが取れます。

二層設定では、この組み合わせは以下のフラックスに相当します：

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
