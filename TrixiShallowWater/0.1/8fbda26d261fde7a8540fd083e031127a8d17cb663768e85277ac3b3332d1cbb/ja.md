```
flux_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterMultiLayerEquations1D)
```

全エネルギー保存（MLSWEの数学的エントロピー）分割形式で、静水圧は含まれていません。底面の地形がゼロでない場合、このスキームは非保存的な [`flux_nonconservative_ersing_etal`](@ref) と併用することで良好にバランスが取れます。

エントロピー安定な定式化を得るために、`surface_flux` を `FluxPlusDissipation(flux_ersing_etal, DissipationLocalLaxFriedrichs()), flux_nonconservative_ersing_etal` と設定することができます。

二層設定では、この組み合わせは以下のフラックスに相当します：

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
